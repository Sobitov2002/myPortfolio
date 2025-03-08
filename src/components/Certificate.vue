<template>
    <div class="certificates">
        <h2 class="text-2xl text-white font-bold mb-4">My Certificates</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-10">
            <div v-for="certificate in certificates" :key="certificate.id" class="certificate-card"
                @click="openModal(certificate)">
                <img :src="certificate.image" :alt="certificate.title" class="certificate-image" />
                <h3 class="text-lg font-semibold mt-2">{{ certificate.title }}</h3>
                <p class="text-gray-500">{{ certificate.issuer }} - {{ certificate.year }}</p>
            </div>
        </div>

        <!-- Modal (sertifikatni katta ekranda ko‘rsatish) -->
        <div v-if="selectedCertificate" class="modal-overlay" @click="closeModal">
            <div class="modal-content" @click.stop>
                <button class="close-btn" @click="closeModal">✖</button>
                <img :src="selectedCertificate.image" class="modal-image" />
                <h3 class="text-xl font-bold mt-4">{{ selectedCertificate.title }}</h3>
                <p class="text-gray-500">{{ selectedCertificate.issuer }} - {{ selectedCertificate.year }}</p>
                <a :href="selectedCertificate.link" target="_blank" class="text-blue-500 hover:underline">Sertifikatni
                    ko'rish</a>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const certificates = ref([
    {
        id: 1,
        title: "IBM Cybersecurity Analyst",
        issuer: "IBM",
        image: "https://ik.imagekit.io/vtroph5l9/Product/my%20Image/Coursera%20AY4V393PURJ9_page-0001.jpg?updatedAt=1741425143246",
        link: "https://www.coursera.org/account/accomplishments/professional-cert/AY4V393PURJ9"
    },
    {
        id: 2,
        title: "Google Advanced Data Analytics",
        issuer: "Udemy",
        image: "https://ik.imagekit.io/vtroph5l9/Product/my%20Image/Coursera%20YIF1WPBS27DO_page-0001.jpg?updatedAt=1741425143171",
        link: "https://www.coursera.org/account/accomplishments/professional-cert/YIF1WPBS27DO"
    },
    {
        id: 3,
        title: "IBM Full Stack Software Developer",
        issuer: "Coursera",
        image: "https://ik.imagekit.io/vtroph5l9/Product/my%20Image/2%20IBM_page-0001.jpg?updatedAt=1741425143264",
        link: "https://www.coursera.org/account/accomplishments/professional-cert/RWZ6QB2L2TZK"
    }
]);

const selectedCertificate = ref(null);

const openModal = (certificate) => {
    selectedCertificate.value = certificate;
};

const closeModal = () => {
    selectedCertificate.value = null;
};
</script>

<style scoped>
.certificates {
    padding: 20px;
}

.certificate-card {
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 16px;
    text-align: center;
    background: white;
    transition: transform 0.2s;
    cursor: pointer;
}

.certificate-card:hover {
    transform: scale(1.05);
}

.certificate-image {
    width: 100%;
    height: auto;
    border-radius: 8px;
}

/* Modal */
.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.6);
    display: flex;
    justify-content: center;
    align-items: center;
}

.modal-content {
    background: white;
    padding: 20px;
    border-radius: 8px;
    text-align: center;
    position: relative;
    max-width: 500px;
}

.modal-image {
    width: 100%;
    border-radius: 8px;
}

.close-btn {
    position: absolute;
    top: 10px;
    right: 10px;
    background: none;
    border: none;
    font-size: 20px;
    cursor: pointer;
}
</style>
