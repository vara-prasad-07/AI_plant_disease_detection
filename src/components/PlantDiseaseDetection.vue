<template>
    <div class="bg-gray-100 min-h-screen flex flex-col">
      <!-- Navbar -->
      <nav class="bg-green-600 p-4 text-white">
        <div class="container mx-auto flex justify-between items-center">
          <h1 class="text-2xl font-bold">Plant Disease Detection</h1>
          <ul class="flex space-x-6">
            <li>
              <a href="#upload" class="hover:underline">Upload</a>
            </li>
            <li>
              <a href="#description" class="hover:underline">About</a>
            </li>
            <li>
              <a href="#how-to-use" class="hover:underline">How to Use</a>
            </li>
          </ul>
        </div>
      </nav>
  
      <!-- About / Description Section -->
      <section id="description" class="py-16 bg-gray-50">
        <div class="container mx-auto px-4">
          <h2 class="text-3xl font-semibold text-center mb-6">
            About Our Project
          </h2>
          <p class="text-lg text-gray-700 text-center mb-6">
            Our Plant Disease Detection system leverages cutting-edge AI...
          </p>
        </div>
      </section>
  
      <!-- Development Section -->
      <section id="development" class="py-16 bg-gray-50">
        <div class="container mx-auto px-4">
          <h2 class="text-3xl font-semibold text-center mb-6">
            How We Developed the Solution
          </h2>
          <ul class="list-disc list-inside text-lg text-gray-700 space-y-4">
            <li>
              <strong>Cutting-Edge Machine Learning Approach:</strong>
              Leveraged the power of
              <span class="text-green-600">Convolutional Neural Networks (CNN)</span> ...
            </li>
            <li>
              <strong>Robust Dataset Preparation:</strong>
              Curated a comprehensive dataset ...
            </li>
            <li>
              <strong>Rigorous Model Training:</strong>
              Achieved optimal accuracy ...
            </li>
            <li>
              <strong>Integration of AI and User Interface:</strong>
              Built an intuitive web interface using
              <span class="text-green-600">Flask</span> ...
            </li>
            <li>
              <strong>Focus on Real-World Impact:</strong>
              Designed the solution to be scalable...
            </li>
          </ul>
        </div>
      </section>
  
      <!-- Upload Section -->
      <section
        id="upload"
        class="flex-grow flex flex-col justify-center items-center bg-white py-16"
      >
        <div
          class="bg-gray-200 p-6 rounded-lg shadow-lg w-1/2 text-center section_1"
          @dragover.prevent
          @drop.prevent="handleDrop"
        >
          <h2 class="text-2xl font-semibold mb-4">Upload Your Crop Image</h2>
          <form @submit.prevent="onSubmit">
            <div
              class="border-dashed border-4 border-gray-300 rounded-lg p-6 bg-gray-100"
              @dragover.prevent
              @drop.prevent="handleDrop"
            >
              <p class="text-gray-500 mb-4">Drag and drop your image here</p>
              <!-- Hidden Input -->
              <input
                ref="imageInput"
                type="file"
                class="hidden"
                accept="image/*"
                @change="handleFileSelect"
              />
              <!-- Trigger Button -->
              <label
                class="cursor-pointer px-4 py-2 bg-green-500 text-white rounded hover:bg-green-600"
                @click="browseFile"
              >
                Browse File
              </label>
            </div>
            <!-- Preview -->
            <div id="preview" class="mt-4">
              <img
                v-if="previewUrl"
                :src="previewUrl"
                alt="Uploaded Image"
                class="max-w-full h-auto rounded-lg shadow-lg mx-auto"
              />
            </div>
            <!-- Predict Button -->
            <button
              type="submit"
              class="mt-4 px-4 py-2 bg-green-500 text-white rounded hover:bg-green-600"
            >
              Predict
            </button>
          </form>
  
          <!-- Loading / Result -->
          <div
            id="loading"
            class="mt-4 text-lg font-semibold text-gray-700"
            v-if="isLoading"
          >
            Loading...
          </div>
          <div id="result" class="mt-4 text-lg font-semibold text-gray-700">
            {{ resultMessage }}
          </div>
        </div>
      </section>
  
      <!-- How to Use Section -->
      <section id="how-to-use" class="py-16 bg-white">
        <div class="container mx-auto px-4">
          <h2 class="text-3xl font-semibold text-center mb-6">How to Use</h2>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
            <div class="p-6 bg-gray-100 rounded-lg shadow-lg text-center">
              <h3 class="text-xl font-bold mb-2">Step 1</h3>
              <p class="text-gray-600">
                Drag and drop or upload your plant image using the upload box.
              </p>
            </div>
            <div class="p-6 bg-gray-100 rounded-lg shadow-lg text-center">
              <h3 class="text-xl font-bold mb-2">Step 2</h3>
              <p class="text-gray-600">
                Click the "Predict" button to analyze the image.
              </p>
            </div>
            <div class="p-6 bg-gray-100 rounded-lg shadow-lg text-center">
              <h3 class="text-xl font-bold mb-2">Step 3</h3>
              <p class="text-gray-600">
                View the results and take necessary action based on the prediction.
              </p>
            </div>
          </div>
        </div>
      </section>
    </div>
  </template>
  
  <script>
  export default {
    name: "PlantDiseaseDetection",
    data() {
      return {
        previewUrl: null,
        selectedFile: null,
        isLoading: false,
        resultMessage: ""
      };
    },
    methods: {
      browseFile() {
        // Triggers the hidden file input click
        this.$refs.imageInput.click();
      },
      handleFileSelect(event) {
        const file = event.target.files[0];
        this.loadPreview(file);
      },
      handleDrop(event) {
        // Handle drag-and-drop file
        const file = event.dataTransfer.files[0];
        if (file) {
          this.$refs.imageInput.files = event.dataTransfer.files;
          this.loadPreview(file);
        }
      },
      loadPreview(file) {
        if (!file) return;
  
        this.selectedFile = file;
        this.resultMessage = "";
  
        const reader = new FileReader();
        reader.onload = (e) => {
          this.previewUrl = e.target.result;
        };
        reader.readAsDataURL(file);
      },
      async onSubmit() {
        if (!this.selectedFile) {
          this.resultMessage = "Please upload an image file.";
          return;
        }
  
        this.isLoading = true;
        this.resultMessage = "";
  
        try {
          const formData = new FormData();
          formData.append("file", this.selectedFile);
  
          const response = await fetch("http://127.0.0.1:5000/predict", {
            method: "POST",
            body: formData
          });
  
          if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
          }
  
          const data = await response.json();
          if (data.error) {
            this.resultMessage = `Error: ${data.error}`;
          } else {
            const labels = { 0: "Healthy", 1: "Powdery", 2: "Rust" };
            const predictedClass = labels[data.predicted_class] || "Unknown";
            this.resultMessage = `Prediction: ${predictedClass}`;
          }
        } catch (error) {
          this.resultMessage = error.message;
        } finally {
          this.isLoading = false;
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .section_1:hover {
    box-shadow: 0px 25px 60px 40px rgba(0, 0, 0, 0.5);
  }
  </style>
  