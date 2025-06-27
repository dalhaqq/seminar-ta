---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Seminar Hasil Abdalhaqq Muhammad Saih

# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# open graph
# seoMeta:
#  ogImage: https://cover.sli.dev
---

## Sistem Rekomendasi Kursus Pemrograman Online Berdasarkan Roadmap Berbasis Website Menggunakan Kombinasi Metode Keyword Search dan Semantic Search

Abdalhaqq Muhammad Saih | H1D020068

|||
|:-:|:-:|
|Dosen Pembimbing 1|Dosen Pembimbing 2|
|Dr. Ir. Lasmedi Afuan, S.T., M.Cs.|Mochammad Agri Triansyah, M.Kom.|


<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: cover
background: https://cover.sli.dev

---
# BAB I
## PENDAHULUAN
---
layout: two-cols-header
transition: fade-out
---

# Latar Belakang
::left::

![Udemy Growth of Courses](https://www.classcentral.com/report/wp-content/uploads/2023/01/2024-11-Udemy-Growth-of-Courses.png)

::right::
<div class="ml-10">
<v-clicks>

- **Era digital**: Platform pembelajaran online (Udemy, Coursera) jadi sumber utama peningkatan keterampilan.

- **Udemy**: Katalog kursus terbesar (262.000+ kursus, 85.787 di kategori teknologi per Nov 2024).

- **Tantangan**: Kebingungan pengguna mencari kursus relevan di tengah jumlah yang eksponensial.

- **Solusi**: Sistem rekomendasi kursus yang efektif.
</v-clicks>
</div>
---
transition: fade-out
---
# Latar Belakang
<br>

- **Riset sebelumnya**:
<v-clicks>

  - Menggabungkan content-based, course-based collaborative filtering, dan static profile-based collaborative filtering (Talaghzi dkk., 2023).

  - Menggunakan model kepribadian RIASEC Holland untuk mahasiswa sarjana (Saleh & Julian, 2023).

  - Kesenjangan: Pendekatan umum, belum mempertimbangkan konteks belajar terstruktur seperti roadmap.

  - Potensi word embedding: Memahami makna semantik teks (Attia dkk., 2023; Chairat dkk., 2023).

  - Integrasi roadmap: Usulan sistem rekomendasi textbook berdasarkan ontologi skill (Motegi & Fukuta, 2023) – masih konseptual.
</v-clicks>
---
transition: fade-out
---

# Latar Belakang
<br>
<br>
<br>

<v-clicks>

- **Tujuan penelitian ini**: Mengembangkan aplikasi rekomendasi kursus berbasis roadmap dengan pendekatan kombinasi (*keyword search* + *semantic search*).

- **Metode**: Reciprocal Rank Fusion (RRF) untuk integrasi hasil.

- **Harapan**: Membantu pengguna menemukan kursus & memandu dalam roadmap pembelajaran.
</v-clicks>
---
transition: fade-out
---

# Rumusan Masalah
<br>
<br>
<br>
<v-clicks>

- Bagaimana mengintegrasikan roadmap pembelajaran ke dalam sistem rekomendasi kursus untuk rekomendasi terstruktur? 

- Bagaimana implementasi kombinasi *keyword search* dan *semantic search* untuk akurasi rekomendasi?

</v-clicks>
---
transition: fade-out
---

# Batasan Masalah
<br>
<br>
<v-clicks>

💻 &nbsp;&nbsp; **Bahasa pemrograman**: JavaScript 

📊 &nbsp;&nbsp; **Data**: Kursus Udemy & roadmap.sh 

📚 &nbsp;&nbsp; **Alur pembelajaran**: Frontend developer & Backend developer 

🔗 &nbsp;&nbsp; **Pengambilan data**: API Udemy & website roadmap.sh 

🔄 &nbsp;&nbsp; **Metode**: Full-text search & text similarity digabung dengan Reciprocal Rank Fusion 

🌐 &nbsp;&nbsp; **Implementasi sistem**: Next.js & PostgreSQL

</v-clicks>
---
transition: fade-out
---

# Tujuan Penelitian
<br>
<br>
<br>
<v-clicks>

- Membangun sistem rekomendasi kursus yang mengintegrasikan roadmap pembelajaran untuk rekomendasi terstruktur sesuai tujuan karier pengguna. 

- Mengimplementasikan pendekatan kombinasi keyword search dan semantic search untuk meningkatkan akurasi dan relevansi rekomendasi kursus.

</v-clicks>

---
layout: cover
background: https://cover.sli.dev
---

# BAB II
## TINJAUAN PUSTAKA
---
transition: fade-out
---

# Landasan Teori

|**Sistem Rekomendasi**|**roadmap.sh**|**Semantic Search**|
|:--|:--|:--|
|Sistem rekomendasi adalah pendukung keputusan yang menyarankan item relevan kepada pengguna, membantu mereka mendapatkan barang berharga dari koleksi yang besar. Sistem ini umumnya berjalan dalam tiga tahap: pemodelan (persiapan data), prediksi (memprediksi peringkat atau skor yang tidak diketahui), dan rekomendasi (menyaring dan mengusulkan item baru yang sesuai).|Roadmap.sh adalah platform yang berisi roadmap, rencana belajar, jalur, dan sumber daya yang dikurasi komunitas untuk pengembang. Situs ini menyediakan roadmap berdasarkan peran (role) dan keahlian (skill), memberikan panduan bagi pengembang yang bingung tentang langkah pembelajaran selanjutnya. Awalnya berupa grafik visual di GitHub, kemudian berkembang menjadi roadmap interaktif.| Pencarian semantik adalah teknik dalam pemrosesan bahasa alami (NLP) yang bertujuan meningkatkan relevansi hasil pencarian dengan memahami makna dan konteks dari pertanyaan pengguna dan teks yang tersedia. Metode ini menggunakan model pencarian rapat (dense retrieval) yang memetakan pertanyaan dan data teks ke dalam ruang vektor, sehingga dapat mengukur kesamaan semantik secara lebih efektif.|

---
transition: fade-out
---

# Landasan Teori

|**Text Embedding**|**Reciprocal Rank Fusion (RRF)**|**PostgreSQL**|
|:--|:--|:--|
|Text embedding adalah representasi vektor dari bahasa alami yang menyandikan informasi semantiknya. Representasi ini banyak digunakan dalam berbagai tugas NLP seperti pengambilan informasi, menjawab pertanyaan, dan rekomendasi item. Setiap kata, frasa, atau kalimat direpresentasikan sebagai titik dalam ruang vektor multidimensi, di mana kedekatan antar titik mencerminkan kemiripan semantik.|Reciprocal Rank Fusion (RRF) adalah metode efektif untuk menggabungkan peringkat dokumen yang berasal dari sistem pengambilan informasi yang berbeda. RRF mengintegrasikan berbagai hasil peringkat untuk menghasilkan daftar rekomendasi yang lebih komprehensif dan relevan.|PostgreSQL adalah sistem database relasional objek open-source yang kuat, dikenal karena arsitekturnya yang terbukti, keandalan, integritas data, dan fitur yang kuat. PostgreSQL mendukung fitur full-text search dan memiliki ekstensi seperti pgvector yang memungkinkan penyimpanan dan operasi data vektor, keduanya penting untuk pencarian dalam penelitian ini.|

---
transition: fade-out
---

# Penelitian Terdahulu

<div class="h-100 overflow-y-auto">

| No | Judul, Peneliti, Tahun | Hasil | Persamaan | Perbedaan |
|---|---|---|---|---|
| 1. | Development Of Undergraduate Students Course Recommender System (Saleh & Julian, 2023) | Sistem rekomendasi kursus dalam bentuk website. 9 dari 15 responden menyatakan bahwa mereka mendapatkan kursus yang cocok. | Ruang lingkup yang sama yaitu sistem rekomendasi kursus berbasis website | Rekomendasi dilakukan menggunakan model RIASEC Holland |
| 2. | A Proposed Model for Enhancing Product Recommendation Based on Word Embedding (Attia dkk., 2023) | Model gabungan word embedding, random forest, dan decision tree. Uji coba pada data baru mendapat nilai accuracy 0.965, precision 0.83, dan recall 0.922. | Ruang lingkup besarnya sama yaitu rekomendasi. Salah satu metode yang digunakan yaitu embedding. | Embedding digabungkan dengan model random forest dan decision tree. Model embedding yang digunakan yaitu kombinasi Word2Vec dan GloVe. |
| 3. | Medication Recommendation using Word Embedding and Recurrent Neural Network (Chairat dkk., 2023) | Model rekomendasi obat menggunakan word embedding dan recurrent neural network. Untuk Word2Vec skor F1 cenderung menurun seiring meningkatnya level ATC, sementara untuk FastText cukup konsisten. | Ruang lingkup besarnya sama yaitu rekomendasi. Salah satu metode yang digunakan yaitu embedding. | Embedding dikombinasikan dengan recurrent neural network. Terdapat 2 model embedding yang digunakan sebagai perbandingan yaitu Word2Vec dan FastText. |
| 4. | A Combined E-Learning Course Recommender System (Talaghzi dkk., 2023) | Sistem rekomendasi kursus dalam bentuk website. Menggabungkan pendekatan content-based recommendation, course-based collaborative filtering, dan static profile-based collaborative filtering membantu mengatasi kelemahan seperti overspecialization dan cold-start. | Ruang lingkup yang sama yaitu sistem rekomendasi kursus berbasis website. Menggunakan gabungan dari beberapa metode untuk meningkatkan relevansi hasil rekomendasi. | Model yang digunakan yaitu content-based recommendation, course-based collaborative filtering, dan static profile-based collaborative filtering. |
| 5. | A Preliminary Implementation of a Textbook Recommendation System for Programming Skill Education using Skill Ontology (Motegi & Fukuta, 2023) | Prototipe antarmuka pengguna sistem rekomendasi textbook dalam bentuk website. Pendekatan awal memanfaatkan ontologi untuk menilai apakah suatu textbook mengandung penjelasan yang dibutuhkan untuk mempelajari suatu skill. | Ruang lingkup yang sama yaitu rekomendasi media pembelajaran pemrograman dalam bentuk website. Menggunakan roadmap pada situs roadmap.sh sebagai acuan. | Masih berupa pendekatan awal dan pembuatan prototipe antarmuka pengguna. |
| 6. | An adaptable and personalized framework for top-N course recommendations in online learning (Amin dkk., 2024) | Mengusulkan kerangka kerja Deep Reinforcement Learning (DRL) dengan model Actor-Critic bernama DRR untuk rekomendasi kursus di Massive Open Online Courses (MOOC). Hasil eksperimen pada dataset Coursera menunjukkan model DRR mengungguli model dasar lainnya (seperti MLP, NMF, SVD++, DQN) dalam metrik evaluasi seperti HR@N, NDCG@N, recall@N, dan precision@N. | Ruang lingkup yang sama yaitu sistem rekomendasi kursus. Menggunakan word embedding (GloVe) untuk ekstraksi fitur dari ulasan teks. | Model utama berbasis Deep Reinforcement Learning (DRL) dengan pendekatan multi-agen, yang memperlakukan rekomendasi sebagai proses pengambilan keputusan sekuensial. Model ini secara dinamis beradaptasi dengan preferensi, sentimen, dan gaya belajar pengguna. |
</div>
---
layout: cover
background: https://cover.sli.dev
---

# BAB III
## METODE PENELITIAN

---
transition: fade-out
---
# Metode Penelitian

<img src="./metode.png" alt="Metodologi Penelitian" class="h-100">


---
transition: fade-out
---
# Pengumpulan Data

<img src="./data.png" alt="Metodologi Penelitian" class="h-100">

---
transition: fade-out
---
# Pemrosesan Data

<img src="./data2.png" alt="Metodologi Penelitian" class="h-100">

---
transition: fade-out
---
# Perancangan Algoritma

<img src="./algoritma.png" alt="Metodologi Penelitian" class="h-100">

---
transition: fade-out
---

# Implementasi Sistem

* Aplikasi rekomendasi dikembangkan dalam bentuk *website* menggunakan bahasa pemrograman JavaScript dengan *runtime* Node.js.
* *Framework* yang digunakan adalah Next.js.
* Database yang digunakan adalah PostgreSQL dengan tambahan ekstensi `pgvector`.
* `pgvector` adalah ekstensi *open-source* untuk PostgreSQL yang menambahkan kemampuan untuk menyimpan dan melakukan operasi pada data vektor.
* Ekstensi ini sangat penting dalam aplikasi rekomendasi karena memungkinkan database untuk bekerja dengan representasi numerik dari teks dan konten.

---
transition: fade-out
---

# Pengujian Sistem

* Setelah sistem berhasil dibuat, dilakukan pengujian fungsional dan pengujian relevansi hasil rekomendasi.
* **Pengujian fungsional** dilakukan secara otomatis dengan pendekatan *end-to-end* menggunakan *framework* Cypress.
* **Pengujian relevansi rekomendasi** dilakukan dengan metrik *Precision at K* (P@K).
* *Precision at K* (P@K) adalah metrik evaluasi yang mengukur proporsi item relevan dalam K rekomendasi teratas yang diberikan sistem.
* Pengujian relevansi rekomendasi dilakukan pada hasil rekomendasi berdasarkan *keyword search*, *semantic search*, serta gabungan dari keduanya sebagai perbandingan.

---
layout: cover
background: https://cover.sli.dev
---

# BAB IV
## HASIL DAN PEMBAHASAN
---
transition: fade-out
---

# Pengumpulan Data
roadmap.sh

<div class="text-center">
  <br><br>
  <br>
  <div class="grid grid-rows-2 gap-4">
    <a href="https://roadmap.sh/frontend" target="_blank" class="text-blue-500 hover:text-blue-700 text-lg">
      🎨 Frontend Developer
    </a>
    <a href="https://roadmap.sh/backend" target="_blank" class="text-green-500 hover:text-green-700 text-lg">
      ⚙️ Backend Developer
    </a>
  </div>
</div>
---
transition: fade-out
---
<style>
.slidev-code, .slidev-monaco-container-inner {
  max-height: 400px !important;
}
</style>

# Pengumpulan Data
roadmap.sh

```js {1-2|4-5|7-8|10,11,21,22|12-20|24,25,35,36|26-34}
const browser = await chromium.launch({ headless: false });
const page = await browser.newPage();

await page.goto(`https://roadmap.sh/${roadmap}`, { waitUntil: 'domcontentloaded' });
await page.waitForTimeout(5000); // Wait for the page to load completely

const topics = await page.$$('[data-type="topic"]');
const subtopics = await page.$$('[data-type="subtopic"]');

const topicContents = await Promise.all(
    topics.map(async topic => {
        const title = await topic.getAttribute('data-title');
        const node = await topic.getAttribute('data-node-id');
        const url = `https://roadmap.sh/${roadmap}/${title.toLowerCase().replace(/[^a-z0-9\s\-]/g, '').replace(/\s/g, '-')}@${node}`;
        return axios.get(url)
            .then(res => {
                const content = res.data.match(/<p>(.*?)<\/p>/)[0];
                return { title, content };
            });
        }
    )
);

const subtopicContents = await Promise.all(
    subtopics.map(async subtopic => {
        const title = await subtopic.getAttribute('data-title');
        const node = await subtopic.getAttribute('data-node-id');
        const url = `https://roadmap.sh/${roadmap}/${title.toLowerCase().replace(/[^a-z0-9\s\-]/g, '').replace(/\s/g, '-')}@${node}`;
        return axios.get(url)
            .then(res => {
                const content = res.data.match(/<p>(.*?)<\/p>/)[0];
                return { title, content };
            });
        }
    )
);
```

---
transition: fade-out
---

# Pengumpulan Data
roadmap.sh

<iframe src="http://localhost:5000" width="100%" height="85%"></iframe>

---
transition: fade-out
---

# Pengumpulan Data
roadmap.sh

```json
[
  {
    "title": "Internet",
    "content": "<p>The Internet is a global network of interconnected computer networks that use the Internet Protocol Suite (TCP/IP) to communicate. It enables the exchange of data, information, and services across the world, connecting billions of devices and users. The Internet has revolutionized communication, commerce, education, and entertainment, becoming an integral part of modern society. It supports various applications and services, from web browsing and instant messaging to streaming media and online gaming. While offering unprecedented access to information and connectivity, the Internet also raises concerns about privacy, security, and digital divide issues.</p>",
    "subtopics": [
      {
        "title": "How does the internet work?",
        "content": "<p>The Internet works through a global network of interconnected computers and servers, communicating via standardized protocols. Data is broken into packets and routed through various network nodes using the Internet Protocol (IP). These packets travel across different physical infrastructures, including fiber optic cables, satellites, and wireless networks. The Transmission Control Protocol (TCP) ensures reliable delivery and reassembly of packets at their destination. Domain Name System (DNS) servers translate human-readable website names into IP addresses. When you access a website, your device sends a request to the appropriate server, which responds with the requested data. This process, facilitated by routers, switches, and other networking equipment, enables the seamless exchange of information across vast distances, forming the backbone of our digital communications.</p>"
      },
      {
        "title": "What is HTTP?",
        "content": "<p>HTTP (Hypertext Transfer Protocol) is the foundation of data communication on the World Wide Web. It’s an application-layer protocol that defines how messages are formatted and transmitted between web browsers and servers. HTTP operates on a request-response model: clients (usually web browsers) send requests to servers, which then respond with the requested data. The protocol is stateless, meaning each request is independent of any previous requests. HTTP supports various methods (GET, POST, PUT, DELETE, etc.) for different types of interactions with resources. HTTPS is the secure version of HTTP, using encryption to protect data in transit. HTTP/2 and HTTP/3 are more recent versions, offering improved performance through features like multiplexing and header compression. Understanding HTTP is crucial for web development, as it underpins how web applications communicate and function.</p>"
      },
      {
        "title": "What is Domain Name?",
        "content": "<p>A domain name is a human-readable address used to identify and access websites on the internet. It serves as a more memorable alternative to the numerical IP addresses that computers use to locate web servers. Domain names consist of two main parts: the second-level domain (usually the website or organization name) and the top-level domain (such as .com, .org, or .net). They are registered through domain registrars and must be unique within their top-level domain. Domain names are crucial for branding, marketing, and establishing an online presence. The Domain Name System (DNS) translates domain names into IP addresses, allowing users to access websites by typing in familiar names rather than complex number sequences. Domain names can be customized, transferred, and renewed, playing a vital role in the structure and accessibility of the World Wide Web.</p>"
      },
      {
        "title": "What is hosting?",
        "content": "<p>Web hosting is a service that allows individuals and organizations to make their websites accessible on the internet. It involves storing website files on powerful computers called servers, which are connected to a high-speed network. When users enter a domain name in their browser, the web host serves the website’s content. Hosting services range from shared hosting (where multiple websites share server resources) to dedicated hosting (where a server is exclusively used by one client). Other types include VPS (Virtual Private Server) hosting, cloud hosting, and managed WordPress hosting. Web hosts typically provide additional services such as email hosting, domain registration, SSL certificates, and technical support. The choice of web hosting impacts a website’s performance, security, and scalability, making it a crucial decision for any online presence.</p>"
      },
      {
        "title": "DNS and how it works?",
        "content": "<p>DNS (Domain Name System) is a hierarchical, decentralized naming system for computers, services, or other resources connected to the Internet or a private network. It translates human-readable domain names (like <a href=\"http://www.example.com\" rel=\"noopener noreferrer nofollow\" target=\"_blank\">www.example.com</a>) into IP addresses (like 192.0.2.1) that computers use to identify each other. DNS servers distributed worldwide work together to resolve these queries, forming a global directory service. The system uses a tree-like structure with root servers at the top, followed by top-level domain servers (.com, .org, etc.), authoritative name servers for specific domains, and local DNS servers. DNS is crucial for the functioning of the Internet, enabling users to access websites and services using memorable names instead of numerical IP addresses.</p>"
      },
      {
        "title": "Browsers and how they work?",
        "content": "<p>A web browser is a software application that enables a user to access and display web pages or other online content through its graphical user interface.</p>"
      }
    ]
  },
  {
    "title": "HTML",
    "content": "<p>HTML (Hypertext Markup Language) is the standard markup language used to create web pages and web applications. It provides a structure for content on the World Wide Web, using a system of elements and attributes to define the layout and content of a document. HTML elements are represented by tags, which browsers interpret to render the visual and auditory elements of a web page. The language has evolved through several versions, with HTML5 being the current standard, introducing semantic elements, improved multimedia support, and enhanced form controls. HTML works in conjunction with CSS for styling and JavaScript for interactivity, forming the foundation of modern web development.</p>",
    "subtopics": [
      {
        "title": "Learn the basics",
        "content": "<p>HTML stands for HyperText Markup Language. It is used on the frontend and gives the structure to the webpage which you can style using CSS and make interactive using JavaScript.</p>"
      },
      {
        "title": "Writing Semantic HTML",
        "content": "<p>Semantic HTML refers to the use of HTML markup to reinforce the meaning of web content, rather than merely defining its appearance. It involves using HTML elements that clearly describe their purpose and content. Semantic HTML improves accessibility, SEO, and code readability. Key elements include <code>&#x3C;header></code>, <code>&#x3C;nav></code>, <code>&#x3C;main></code>, <code>&#x3C;article></code>, <code>&#x3C;section></code>, <code>&#x3C;aside></code>, and <code>&#x3C;footer></code>. It also encompasses using appropriate heading levels (<code>&#x3C;h1></code> to <code>&#x3C;h6></code>), lists (<code>&#x3C;ul></code>, <code>&#x3C;ol></code>,<code>&#x3C;li></code>), and data tables (<code>&#x3C;table></code>, <code>&#x3C;th></code>, <code>&#x3C;td></code>). Semantic HTML helps screen readers interpret page content, enables better browser rendering, and provides clearer structure for developers. By using semantically correct elements, developers create more meaningful, accessible, and maintainable web documents that are easier for both humans and machines to understand and process.</p>"
      },
      {
        "title": "Forms and Validations",
        "content": "<p>Before submitting data to the server, it is important to ensure all required form controls are filled out, in the correct format. This is called client-side form validation, and helps ensure data submitted matches the requirements set forth in the various form controls.</p>"
      },
      {
        "title": "Accessibility",
        "content": "<p>Website accessibility is the practice of designing and developing websites that can be used by everyone, including people with disabilities. It involves implementing features and standards that make web content perceivable, operable, understandable, and robust for all users, regardless of their physical or cognitive abilities. This includes providing text alternatives for images, ensuring keyboard navigation, using sufficient color contrast, offering captions for audio content, and creating a consistent and predictable layout. Adhering to accessibility guidelines not only improves usability for people with disabilities but also enhances the overall user experience for all visitors while potentially increasing a site’s reach and legal compliance.</p>"
      },
      {
        "title": "SEO Basics",
        "content": "<p>SEO (Search Engine Optimization) basics involve strategies to improve a website’s visibility and ranking in search engine results. Key elements include creating relevant, high-quality content, proper use of keywords, optimizing meta tags and URLs, ensuring mobile-friendliness, improving site speed, and building quality backlinks. SEO also focuses on user experience, including easy navigation and responsive design. Technical aspects like XML sitemaps, HTTPS security, and structured data markup play crucial roles. Understanding user intent, regularly updating content, and adhering to search engine guidelines are essential practices. Effective SEO combines on-page optimization, off-page tactics, and technical enhancements to increase organic traffic, improve user engagement, and enhance online presence in an increasingly competitive digital landscape.</p>"
      }
    ]
  },
  {
    "title": "CSS",
    "content": "<p>CSS (Cascading Style Sheets) is a styling language used to describe the presentation of a document written in HTML or XML. It defines how elements should be displayed on screen, on paper, or in other media. CSS separates the design from the content, allowing for greater flexibility and control over the layout, colors, and fonts of web pages. It uses a system of selectors to target HTML elements and apply styles to them. CSS supports responsive design through media queries, enabling the creation of layouts that adapt to different screen sizes and devices. The cascade, inheritance, and specificity are key concepts in CSS that determine how styles are applied when multiple rules target the same element. Modern CSS includes features like Flexbox and Grid for advanced layout control, animations, and transitions for creating dynamic user interfaces.</p>",
    "subtopics": [
      {
        "title": "Learn the basics",
        "content": "<p>CSS or Cascading Style Sheets is the language used to style the frontend of any website. CSS is a cornerstone technology of the World Wide Web, alongside HTML and JavaScript.</p>"
      },
      {
        "title": "Making Layouts",
        "content": "<p>Making layouts in web design involves organizing content and visual elements on a page to create an effective and aesthetically pleasing user interface. Modern layout techniques primarily use CSS, with key approaches including:</p>"
      },
      {
        "title": "Responsive Design",
        "content": "<p>Responsive web design is an approach to web development that creates dynamic changes to the appearance of a website, depending on the screen size and orientation of the device being used to view it. It uses fluid grids, flexible images, and CSS media queries to adapt the layout to the viewing environment. The goal is to build web pages that detect the visitor’s screen size and orientation and change the layout accordingly, providing an optimal viewing experience across a wide range of devices, from desktop computers to mobile phones. This approach eliminates the need for a different design and development phase for each new gadget on the market, while ensuring a consistent and intuitive user experience across all devices.</p>"
      }
    ]
  },
  {
    "title": "JavaScript",
    "content": "<p>JavaScript is a high-level, interpreted programming language that is a core technology of the World Wide Web. It allows for dynamic, client-side scripting in web browsers, enabling interactive web pages and user interfaces. JavaScript supports object-oriented, imperative, and functional programming styles. It’s also used server-side through Node.js, for desktop application development with frameworks like Electron, and in various other contexts. The language features dynamic typing, first-class functions, and prototype-based object-orientation. JavaScript’s ubiquity in web development, coupled with its versatility and continuous evolution through ECMAScript standards, has made it one of the most popular programming languages in use today.</p>",
    "subtopics": [
      {
        "title": "Learn the Basics",
        "content": "<p>JavaScript allows you to add interactivity to your pages. Common examples that you may have seen on the websites are sliders, click interactions, popups and so on.</p>"
      },
      {
        "title": "Learn DOM Manipulation",
        "content": "<p>The Document Object Model (DOM) is a programming interface built for HTML and XML documents. It represents the page that allows programs and scripts to dynamically update the document structure, content, and style. With DOM, we can easily access and manipulate tags, IDs, classes, attributes, etc.</p>"
      },
      {
        "title": "Fetch API / Ajax (XHR)",
        "content": "<p>The Fetch API is a modern JavaScript interface for making HTTP requests in web browsers. It provides a more powerful and flexible way to send and receive data compared to older methods like XMLHttpRequest. Fetch uses Promises, allowing for cleaner asynchronous code. It supports various data formats, custom headers, and different types of requests (GET, POST, etc.). The API is designed to be extensible and integrates well with other web technologies. While simpler for basic use cases, Fetch also handles complex scenarios like request cancellation and reading streamed responses. It’s widely supported in modern browsers and has become the standard for network requests in client-side JavaScript applications.</p>"
      }
    ]
  },
  {
    "title": "Version Control Systems",
    "content": "<p>Version Control Systems (VCS) are tools that help developers track and manage changes to code over time. They allow multiple people to work on a project simultaneously, maintaining a history of modifications. Git is the most popular VCS, known for its distributed nature and branching model. Other systems include Subversion (SVN) and Mercurial. VCS enables features like branching for parallel development, merging to combine changes, and reverting to previous states. They facilitate collaboration through remote repositories, pull requests, and code reviews. VCS also provides backup and recovery capabilities, conflict resolution, and the ability to tag specific points in history. By maintaining a detailed record of changes and supporting non-linear development, VCS has become an essential tool in modern software development, enhancing productivity, code quality, and team collaboration.</p>",
    "subtopics": [
      {
        "title": "Git",
        "content": "<p>Git is a distributed version control system designed to handle projects of any size with speed and efficiency. Created by Linus Torvalds in 2005, Git tracks changes in source code during software development, allowing multiple developers to work together on non-linear development. It provides strong support for branching, merging, and distributed development workflows. Git maintains a complete history of all changes, enabling easy rollbacks and comparisons between versions. Its distributed nature means each developer has a full copy of the repository, allowing for offline work and backup. Git’s speed, flexibility, and robust branching and merging capabilities have made it the most widely used version control system in software development, particularly for open-source projects.</p>"
      }
    ]
  },
  {
    "title": "VCS Hosting",
    "content": "<p>Repo hosting services provide platforms for storing, managing, and collaborating on software projects using version control systems, primarily Git. These services offer features like issue tracking, pull requests, code review tools, wikis, and continuous integration/continuous deployment (CI/CD) pipelines. Popular platforms include GitHub, GitLab, Bitbucket, and SourceForge, each with unique offerings. GitHub, owned by Microsoft, is the largest and most widely used, known for its open-source community. GitLab offers a complete DevOps platform with built-in CI/CD. Bitbucket, part of Atlassian’s suite, integrates well with other Atlassian tools. These services facilitate team collaboration, code sharing, and project management, making them integral to modern software development workflows. They also often provide features like access control, branch protection, and integration with various development tools, enhancing the overall development process.</p>",
    "subtopics": [
      {
        "title": "GitHub",
        "content": "<p>GitHub has become a central hub for open-source projects and is widely used by developers, companies, and organizations for both private and public repositories. It was acquired by Microsoft in 2018 but continues to operate as a relatively independent entity. GitHub’s popularity has made it an essential tool in modern software development workflows and a key platform for showcasing coding projects and contributing to open-source software.</p>"
      },
      {
        "title": "GitLab",
        "content": "<p>GitLab is a web-based DevOps platform that provides a complete solution for the software development lifecycle. GitLab emphasizes an all-in-one approach, integrating various development tools into a single platform. It’s available as both a cloud-hosted service and a self-hosted solution, giving organizations flexibility in deployment. GitLab’s focus on DevOps practices and its comprehensive feature set make it popular among enterprises and teams seeking a unified platform for their entire development workflow. While similar to GitHub in many respects, GitLab’s integrated CI/CD capabilities and self-hosting options are often cited as key differentiators.</p>"
      },
      {
        "title": "Bitbucket",
        "content": "<p>Bitbucket is a web-based version control repository hosting service owned by Atlassian. It provides Git and Mercurial version control systems for both open source and private projects. Bitbucket offers features such as pull requests, branch permissions, and in-line commenting for code review. It integrates seamlessly with other Atlassian products like Jira and Trello, facilitating project management and issue tracking. Bitbucket provides both cloud-hosted and self-hosted options, catering to different organizational needs. It supports continuous integration and deployment (CI/CD) through Bitbucket Pipelines.</p>"
      }
    ]
  },
  {
    "title": "Package Managers",
    "content": "<p>Package managers are tools that automate the process of installing, updating, configuring, and removing software packages in a consistent manner. They handle dependency resolution, version management, and package distribution for programming languages and operating systems. Popular package managers include npm for JavaScript, pip for Python, and apt for Debian-based Linux distributions. These tools maintain a centralized repository of packages, allowing developers to easily share and reuse code. Package managers simplify project setup, ensure consistency across development environments, and help manage complex dependency trees. They play a crucial role in modern software development by streamlining workflow, enhancing collaboration, and improving code reusability.</p>",
    "subtopics": [
      {
        "title": "npm",
        "content": "<p>npm (Node Package Manager) is the default package manager for Node.js, providing a vast ecosystem of reusable JavaScript code. It allows developers to easily share, discover, and install packages (libraries and tools) for their projects. npm consists of a command-line interface for package installation and management, and an online repository of open-source packages. It handles dependency management, version control, and script running for Node.js projects. The npm registry is the largest software registry in the world, containing over a million packages. npm’s package.json file defines project metadata and dependencies, enabling reproducible builds across different environments. Despite competition from alternatives like Yarn, npm remains the most widely used package manager in the JavaScript ecosystem.</p>"
      },
      {
        "title": "pnpm",
        "content": "<p>pnpm (performant npm) is a fast, disk-space efficient package manager for JavaScript and Node.js projects. It addresses inefficiencies in npm and Yarn by using a unique approach to storing and linking dependencies. pnpm creates a single, global store for all packages and uses hard links to reference them in project node_modules, significantly reducing disk space usage and installation time. It strictly adheres to package.json specifications, ensuring consistent installs across environments. pnpm offers features like workspace support for monorepos, side-by-side versioning, and improved security through better isolation of dependencies. While less widely adopted than npm or Yarn, pnpm’s performance benefits and efficient disk usage are attracting increasing attention in the JavaScript community.</p>"
      },
      {
        "title": "yarn",
        "content": "<p>Yarn is a fast, reliable, and secure package manager for JavaScript, developed by Facebook as an alternative to npm (Node Package Manager). It addresses issues of consistency, security, and performance in dependency management. Yarn uses a lockfile to ensure consistent installations across different environments and offers parallel installation of packages, significantly speeding up the process. It features offline mode, allowing installation from cached packages, and provides improved network performance through request queuing and retries. Yarn’s focus on security includes checksum verification of every installed package. While it shares many features with npm, Yarn’s emphasis on speed, reliability, and security has made it a popular choice among developers, especially for larger projects. Recent versions of Yarn (Berry) introduce new features like Plug’n’Play for even faster and more efficient package resolution.</p>"
      }
    ]
  },
  {
    "title": "Pick a Framework",
    "content": "<p>Web frameworks are designed to write web applications. Frameworks are collections of libraries that aid in the development of a software product or website. Frameworks for web application development are collections of various tools. Frameworks vary in their capabilities and functions, depending on the tasks set. They define the structure, establish the rules, and provide the development tools required.</p>",
    "subtopics": [
      {
        "title": "React",
        "content": "<p>React is an open-source JavaScript library for building user interfaces, primarily for single-page applications. Developed and maintained by Facebook, it allows developers to create reusable UI components that efficiently update and render as data changes. React uses a virtual DOM for performance optimization and supports a unidirectional data flow. Its component-based architecture promotes modularity and reusability. React’s ecosystem includes tools like Redux for state management and React Native for mobile app development. The library’s declarative nature, efficient rendering, and strong community support have made it one of the most popular choices for front-end development in modern web applications.</p>"
      },
      {
        "title": "Vue.js",
        "content": "<p>Vue.js is a progressive JavaScript framework for building user interfaces. It’s designed to be incrementally adoptable, allowing developers to integrate it into projects gradually. Vue uses a template-based approach with a virtual DOM for efficient rendering. It features a reactive and composable component system, making it easy to organize and reuse code. Vue’s core library focuses on the view layer, but it can be easily extended with official and community-built tools for state management, routing, and build tooling. Known for its gentle learning curve and flexibility, Vue has gained popularity for both small projects and large-scale applications. Its performance, lightweight nature, and comprehensive documentation have contributed to its widespread adoption in the web development community.</p>"
      },
      {
        "title": "Angular",
        "content": "<p>Angular is a popular open-source web application framework developed and maintained by Google. It uses TypeScript, a statically typed superset of JavaScript, to build scalable and efficient single-page applications (SPAs). Angular follows a component-based architecture, where the user interface is composed of reusable, self-contained components. The framework provides features like two-way data binding, dependency injection, and a powerful template syntax, which simplify the development of complex web applications. Angular also includes a comprehensive set of tools for testing, routing, and state management, making it a full-fledged solution for front-end development. Its modular structure and emphasis on best practices make it particularly suitable for large-scale enterprise applications.</p>"
      },
      {
        "title": "Svelte",
        "content": "<p>Svelte is a modern JavaScript framework for building user interfaces that takes a unique approach to web development. Unlike traditional frameworks that do most of their work in the browser, Svelte shifts that work into a compile step that happens when you build your app. It compiles your code to efficient vanilla JavaScript, resulting in smaller bundle sizes and better runtime performance. Svelte uses a component-based architecture and features a simple, intuitive syntax that allows developers to write less code. It includes built-in state management, CSS scoping, and animations. Svelte’s approach eliminates the need for a virtual DOM, leading to faster initial loads and updates. Its simplicity and performance benefits have been gaining it increasing popularity in the front-end development community.</p>"
      },
      {
        "title": "Solid JS",
        "content": "<p>SolidJS is a declarative, efficient, and flexible JavaScript library for building user interfaces. It uses a fine-grained reactivity system that updates only what changes, resulting in high performance. SolidJS compiles templates to real DOM nodes and updates them in-place, avoiding the overhead of a virtual DOM. It offers a syntax similar to React, making it familiar to many developers, but with a different underlying mechanism. SolidJS supports JSX, provides built-in state management, and emphasizes composition over inheritance. Its small size and lack of runtime overhead make it particularly suitable for applications requiring high performance. While newer compared to some frameworks, SolidJS is gaining popularity for its simplicity, performance, and developer-friendly approach to reactive programming.</p>"
      },
      {
        "title": "Qwik",
        "content": "<p>Qwik is an open-source front-end framework designed for optimal performance and near-instant loading of web applications. It focuses on delivering a “resumable” application model, where the app can start running with minimal JavaScript downloaded. Qwik achieves this through fine-grained lazy loading, serialization of the application state, and prefetching. It uses a unique approach to hydration, only loading JavaScript for interactive elements when needed. Qwik is built for modern web standards and aims to solve performance issues common in large-scale web applications. While still relatively new compared to established frameworks, Qwik’s innovative approach to performance optimization is garnering attention in the web development community.</p>"
      }
    ]
  },
  {
    "title": "Writing CSS",
    "content": "<p>Modern CSS emphasizes responsive design with techniques like media queries and fluid typography. It also includes methodologies like CSS-in-JS and utility-first frameworks (e.g., Tailwind CSS). Features such as CSS Logical Properties improve internationalization, while CSS Houdini allows for more powerful custom styling. Modern CSS focuses on performance optimization, maintainability, and creating adaptive, accessible designs across various devices and screen sizes, significantly improving the capabilities and efficiency of web styling.</p>",
    "subtopics": [
      {
        "title": "Tailwind",
        "content": "<p>Tailwind CSS is a utility-first CSS framework that provides low-level utility classes to build custom designs without leaving your HTML. It offers a highly customizable set of pre-defined classes for layout, typography, color, and more, allowing rapid UI development. Tailwind emphasizes flexibility and composability, enabling developers to create unique designs without writing custom CSS. It uses a mobile-first approach and includes a built-in purge feature to remove unused styles in production, resulting in smaller file sizes. Tailwind’s philosophy promotes consistency in design while maintaining the freedom to create custom looks. Its popularity has grown due to its efficiency in prototyping and building responsive designs quickly.</p>"
      }
    ]
  },
  {
    "title": "CSS Architecture",
    "content": "<p>CSS architecture refers to the methodologies and organizational strategies used to structure and maintain CSS code in large-scale web projects. It focuses on creating scalable, maintainable, and modular stylesheets to manage the growing complexity of web applications. Key concepts include naming conventions (like BEM or SMACSS), component-based design, separation of concerns, and the use of preprocessors (such as Sass or Less). CSS architecture often employs techniques like CSS modules, utility classes, or CSS-in-JS solutions to improve code reusability and reduce specificity conflicts. The goal is to create a systematic approach to styling that enhances collaboration among developers, reduces code duplication, and facilitates easier updates and maintenance of the visual design across an entire application or website.</p>",
    "subtopics": [
      {
        "title": "BEM",
        "content": "<p>The Block, Element, Modifier methodology (commonly referred to as BEM) is a popular naming convention for classes in HTML and CSS. Developed by the team at Yandex, its goal is to help developers better understand the relationship between the HTML and CSS in a given project.</p>"
      }
    ]
  },
  {
    "title": "CSS Preprocessors",
    "content": "<p>CSS preprocessors are scripting languages that extend the capabilities of standard CSS, allowing developers to write more maintainable and efficient stylesheets. They introduce features like variables, nesting, mixins, functions, and mathematical operations, which are then compiled into standard CSS. Popular preprocessors include Sass, Less, and Stylus. These tools enable developers to organize styles more logically, reuse code more effectively, and create complex CSS structures with less repetition. Preprocessors often support features like partials for modular stylesheets and built-in color manipulation functions. By using a preprocessor, developers can write more DRY (Don’t Repeat Yourself) code, manage large-scale projects more easily, and potentially improve the performance of their stylesheets through optimization during the compilation process.</p>",
    "subtopics": [
      {
        "title": "Sass",
        "content": "<p>Sass (Syntactically Awesome Style Sheets) is a mature, stable, and powerful professional-grade CSS extension language. It extends CSS with features like variables, nested rules, mixins, inline imports, and more, all with fully CSS-compatible syntax. Sass allows for more organized, maintainable, and reusable styles in complex projects. It compiles to clean, standard CSS, supporting two syntaxes: the original indented syntax and the more popular SCSS (Sassy CSS) syntax. Sass provides functionality like control directives for libraries, making it easier to write well-structured, scalable CSS. Its features help reduce repetition in CSS and save time, making it a popular choice among frontend developers for managing large, complex stylesheets.</p>"
      },
      {
        "title": "PostCSS",
        "content": "<p>PostCSS is a tool for transforming CSS with JavaScript plugins. It allows developers to enhance their CSS workflow by automating repetitive tasks, adding vendor prefixes, and implementing future CSS features. PostCSS works as a preprocessor, but unlike Sass or Less, it’s highly modular and customizable. Users can choose from a wide range of plugins or create their own to suit specific needs. Popular plugins include Autoprefixer for adding vendor prefixes, cssnext for using future CSS features, and cssnano for minification. PostCSS integrates well with various build tools and can be used alongside traditional CSS preprocessors. Its flexibility and performance make it a popular choice for optimizing CSS in modern web development workflows.</p>"
      }
    ]
  },
  {
    "title": "Build Tools",
    "content": "<p>Build tools are software utilities designed to automate the process of creating executable applications from source code. They handle tasks such as compiling, linking, minifying, and bundling code, as well as running tests and managing dependencies. Common build tools include Make, Gradle, Maven, Webpack, and Gulp. These tools streamline development workflows by reducing manual steps, ensuring consistency across different environments, and optimizing output for production. They often support features like incremental builds, parallel processing, and custom task definitions. Build tools are crucial in modern software development, especially for large-scale projects, as they improve efficiency, reduce errors, and facilitate continuous integration and deployment processes.</p>",
    "subtopics": []
  },
  {
    "title": "Linters and Formatters",
    "content": "<p>Linters and formatters are tools used in software development to improve code quality and consistency. Linters analyze source code to detect programming errors, bugs, stylistic issues, and suspicious constructs, often enforcing a set of predefined or custom rules. Formatters automatically restructure code to adhere to a consistent style, adjusting elements like indentation, line breaks, and spacing. Together, these tools help maintain code standards across projects and teams, enhance readability, catch potential errors early, and reduce the cognitive load on developers during code reviews. Popular examples include ESLint for JavaScript linting and Prettier for code formatting, both of which can be integrated into development workflows and IDEs for real-time feedback and automatic corrections.</p>",
    "subtopics": [
      {
        "title": "Prettier",
        "content": "<p>Prettier is an opinionated code formatter that supports multiple programming languages, including JavaScript, TypeScript, CSS, and more. It automatically formats code to adhere to a consistent style, eliminating debates about code formatting in development teams. Prettier parses code and reprints it with its own rules, taking maximum line length into account and wrapping code when necessary. It integrates with most editors and can be run as part of the development workflow or in pre-commit hooks. Prettier’s main benefits include saving time on code reviews, reducing cognitive load for developers, and maintaining a consistent code style across projects. Its “zero-config” philosophy and wide language support have made it a popular tool in modern development environments.</p>"
      },
      {
        "title": "ESLint",
        "content": "<p>ESLint is a popular open-source static code analysis tool for identifying and fixing problems in JavaScript code. It enforces coding standards, detects potential errors, and promotes consistent coding practices across projects. ESLint is highly configurable, allowing developers to define custom rules or use preset configurations. It supports modern JavaScript features, JSX, and TypeScript through plugins. ESLint can be integrated into development workflows through IDE extensions, build processes, or git hooks, providing real-time feedback to developers. Its ability to automatically fix many issues it detects makes it a valuable tool for maintaining code quality and consistency, especially in large teams or projects. ESLint’s extensibility and wide adoption in the JavaScript ecosystem have made it a standard tool in modern JavaScript development.</p>"
      }
    ]
  },
  {
    "title": "Module Bundlers",
    "content": "<p>Module bundlers are development tools that combine multiple JavaScript files and their dependencies into a single file, optimized for web browsers. They resolve and manage dependencies, transform and optimize code, and often support features like code splitting and lazy loading. Popular module bundlers include Webpack, Rollup, and Parcel. These tools address challenges in managing complex JavaScript applications by organizing code into modules, eliminating global scope pollution, and improving load times. Bundlers typically support various file formats, enable the use of modern JavaScript features through transpilation, and integrate with task runners and other build tools. Their primary goal is to streamline the development process and enhance application performance in production environments.</p>",
    "subtopics": [
      {
        "title": "Vite",
        "content": "<p>Vite is a modern build tool and development server designed for fast and lean development of web applications. Created by Evan You, the author of Vue.js, Vite leverages native ES modules in the browser to enable near-instantaneous server start and lightning-fast hot module replacement (HMR). It supports various frameworks including Vue, React, and Svelte out of the box. Vite uses Rollup for production builds, resulting in highly optimized bundles. It offers features like CSS pre-processor support, TypeScript integration, and plugin extensibility. Vite’s architecture, which separates dev and build concerns, allows for faster development cycles and improved developer experience, particularly for large-scale projects where traditional bundlers might struggle with performance.</p>"
      },
      {
        "title": "SWC",
        "content": "<p>The Speedy Web Compiler (SWC) is a fast, extensible JavaScript/TypeScript compiler written in Rust. It’s designed as a faster alternative to Babel for transpiling modern JavaScript code into backwards-compatible versions. SWC can be used for both compilation and bundling, offering significant performance improvements over traditional JavaScript-based tools. It supports latest ECMAScript features, JSX, and TypeScript, and can be configured for custom transformations. SWC is commonly used in development environments to speed up build times and in production builds to optimize code. Its speed and compatibility make it increasingly popular in large-scale JavaScript projects and as a core component in other build tools and frameworks aiming for improved performance.</p>"
      },
      {
        "title": "esbuild",
        "content": "<p>esbuild is a high-performance JavaScript bundler and minifier designed for speed and efficiency. Created by Evan Wallace, it’s written in Go and compiles to native code, making it significantly faster than traditional JavaScript-based build tools. esbuild supports modern JavaScript features, TypeScript, and JSX out of the box, with near-instant bundling times even for large projects. It offers a simple API and command-line interface, making it easy to integrate into existing build pipelines. While primarily focused on speed, esbuild also provides basic code splitting, tree shaking, and source map generation. Its extreme performance makes it particularly suitable for development environments and as a foundation for other build tools, though it may lack some advanced features found in more mature bundlers.</p>"
      },
      {
        "title": "Webpack",
        "content": "<p>Webpack is a popular open-source JavaScript module bundler that transforms, bundles, or packages resources for the web. It takes modules with dependencies and generates static assets representing those modules. Webpack can handle not just JavaScript, but also other assets like CSS, images, and fonts. It uses loaders to preprocess files and plugins to perform a wider range of tasks like bundle optimization. Webpack’s key features include code splitting, lazy loading, and a rich ecosystem of extensions. It supports hot module replacement for faster development and tree shaking to eliminate unused code. While it has a steeper learning curve compared to some alternatives, Webpack’s flexibility and powerful features make it a standard tool in many modern JavaScript development workflows, especially for complex applications.</p>"
      },
      {
        "title": "Rollup",
        "content": "<p>Rollup is a module bundler for JavaScript that compiles small pieces of code into larger, more complex structures. It specializes in producing smaller, more efficient bundles for ES modules. Rollup excels at tree-shaking, eliminating unused code for leaner outputs. It’s particularly well-suited for libraries and applications using the ES module format. Rollup supports various output formats, including UMD and CommonJS, making it versatile for different deployment scenarios. While it may require more configuration than some alternatives, Rollup’s focus on ES modules and its efficient bundling make it popular for projects prioritizing small bundle sizes and modern JavaScript practices.</p>"
      },
      {
        "title": "Parcel",
        "content": "<p>Parcel is a zero-configuration web application bundler that simplifies the process of building and deploying web projects. It supports multiple programming languages and file types out of the box, including JavaScript, CSS, HTML, and various image formats. Parcel automatically analyzes dependencies, transforms code, and optimizes assets without requiring a complex configuration file. It offers features like hot module replacement, code splitting, and tree shaking by default. Parcel’s main selling point is its ease of use and fast build times, achieved through parallel processing and caching. While it may lack some advanced features of more established bundlers like Webpack, Parcel’s simplicity and performance make it an attractive option for rapid prototyping and smaller projects.</p>"
      }
    ]
  },
  {
    "title": "Testing",
    "content": "<p>Testing apps involves systematically evaluating software to ensure it meets requirements, functions correctly, and maintains quality. Key testing types include:</p>",
    "subtopics": [
      {
        "title": "Playwright",
        "content": "<p>Playwright is an open-source automation framework developed by Microsoft for end-to-end testing of web applications. It provides a single API to automate Chromium, Firefox, and WebKit browsers across Windows, macOS, and Linux. Playwright supports multiple programming languages including JavaScript, TypeScript, Python, and .NET. It offers features like auto-waiting, network interception, and mobile emulation. The framework excels in handling modern web apps with dynamic content, providing reliable automation through its ability to wait for elements to be ready before acting on them. Playwright’s cross-browser and cross-platform capabilities, combined with its powerful tooling for debugging and test generation, make it a robust choice for automated testing of web applications.</p>"
      },
      {
        "title": "Cypress",
        "content": "<p>Cypress framework is a JavaScript-based end-to-end testing framework built on top of Mocha – a feature-rich JavaScript test framework running on and in the browser, making asynchronous testing simple and convenient. It also uses a BDD/TDD assertion library and a browser to pair with any JavaScript testing framework.</p>"
      },
      {
        "title": "Vitest",
        "content": "<p>Vitest is a fast and lightweight testing framework for JavaScript and TypeScript projects, designed as a Vite-native alternative to Jest. It leverages Vite’s transformation pipeline and config resolution, offering near-instant test execution and hot module replacement (HMR) for tests. Vitest provides a Jest-compatible API, making migration easier for projects already using Jest. It supports features like snapshot testing, mocking, and code coverage out of the box. Vitest’s architecture allows for parallel test execution and watch mode, significantly speeding up the testing process. Its integration with Vite’s ecosystem makes it particularly well-suited for projects already using Vite, but it can be used in any JavaScript project. Vitest’s focus on speed and developer experience has made it an increasingly popular choice for modern web development workflows.</p>"
      },
      {
        "title": "Jest",
        "content": "<p>Jest is a popular JavaScript testing framework developed by Facebook. It provides a comprehensive solution for unit testing JavaScript code, with a focus on simplicity and minimal configuration. Jest offers features such as automatic mocking, code coverage reporting, and snapshot testing. It supports testing of both synchronous and asynchronous code, and can be used with various JavaScript frameworks and libraries, including React, Angular, and Vue. Jest’s built-in assertion library and test runner make it easy to write and execute tests quickly. Its ability to run tests in parallel and its intelligent test-watching mode contribute to fast test execution, making it a preferred choice for many developers and organizations in the JavaScript ecosystem.</p>"
      }
    ]
  },
  {
    "title": "Authentication Strategies",
    "content": "<p>Authentication strategies are methods or techniques used to verify the identity of a user or system in order to grant access to a protected resource. There are several different authentication strategies that can be used, including:</p>",
    "subtopics": []
  },
  {
    "title": "Web Security Basics",
    "content": "<p>Web security knowledge encompasses understanding and implementing practices to protect websites, web applications, and web services from various cyber threats. Key areas include:</p>",
    "subtopics": [
      {
        "title": "CORS",
        "content": "<p>Cross-Origin Resource Sharing (CORS) is a security mechanism implemented by web browsers to control access to resources (like APIs or fonts) on a web page from a different domain than the one serving the web page. It extends and adds flexibility to the Same-Origin Policy, allowing servers to specify who can access their resources. CORS works through a system of HTTP headers, where browsers send a preflight request to the server hosting the cross-origin resource, and the server responds with headers indicating whether the actual request is allowed. This mechanism helps prevent unauthorized access to sensitive data while enabling legitimate cross-origin requests. CORS is crucial for modern web applications that often integrate services and resources from multiple domains, balancing security needs with the functionality requirements of complex, distributed web systems.</p>"
      },
      {
        "title": "HTTPS",
        "content": "<p>Hypertext transfer protocol secure (HTTPS) is the secure version of HTTP, which is the primary protocol used to send data between a web browser and a website. HTTPS is encrypted in order to increase security of data transfer. This is particularly important when users transmit sensitive data, such as by logging into a bank account, email service, or health insurance provider.</p>"
      },
      {
        "title": "Content Security Policy",
        "content": "<p>Content Security Policy (CSP) is a security standard implemented by web browsers to prevent cross-site scripting (XSS), clickjacking, and other code injection attacks. It works by allowing web developers to specify which sources of content are trusted and can be loaded on a web page. CSP is typically implemented through HTTP headers or meta tags, defining rules for various types of resources like scripts, stylesheets, images, and fonts. By restricting the origins from which content can be loaded, CSP significantly reduces the risk of malicious code execution. It also provides features like reporting violations to help developers identify and fix potential security issues. While powerful, implementing CSP requires careful configuration to balance security with functionality, especially for sites using third-party resources or inline scripts.</p>"
      },
      {
        "title": "OWASP Security Risks",
        "content": "<p>OWASP (Open Web Application Security Project) identifies and ranks the most critical security risks to web applications. The OWASP Top 10 list includes vulnerabilities such as injection flaws, broken authentication, sensitive data exposure, XML external entities (XXE), broken access control, security misconfigurations, cross-site scripting (XSS), insecure deserialization, using components with known vulnerabilities, and insufficient logging and monitoring. These risks represent common attack vectors exploited by malicious actors to compromise web applications and their underlying systems. OWASP provides guidelines and best practices for mitigating these risks, emphasizing the importance of secure coding practices, regular security assessments, and implementing robust security controls throughout the software development lifecycle. Understanding and addressing these risks is crucial for developers and organizations to enhance the security posture of their web applications.</p>"
      }
    ]
  },
  {
    "title": "Web Components",
    "content": "<p>Web Components are a set of standardized browser technologies that allow developers to create reusable, encapsulated HTML elements for web pages and applications. They consist of three main technologies: Custom Elements for defining new HTML tags, Shadow DOM for encapsulating styles and markup, and HTML Templates for declaring fragments of reusable HTML. Web Components enable the creation of modular, shareable components that work across different frameworks and browsers. They provide strong encapsulation, reducing style conflicts and promoting code reuse. While adoption has been slower compared to popular JavaScript frameworks, Web Components offer a standards-based approach to component development, ensuring long-term compatibility and interoperability in web ecosystems.</p>",
    "subtopics": [
      {
        "title": "HTML Templates",
        "content": "<p>The <code>&#x3C;template></code> HTML element is a mechanism for holding HTML that is not to be rendered immediately when a page is loaded but may be instantiated subsequently during runtime using JavaScript. Think of a template as a content fragment that is being stored for subsequent use in the document.</p>"
      },
      {
        "title": "Custom Elements",
        "content": "<p>One of the key features of the Web Components standard is the ability to create custom elements that encapsulate your functionality on an HTML page, rather than having to make do with a long, nested batch of elements that together provide a custom page feature.</p>"
      },
      {
        "title": "Shadow DOM",
        "content": "<p>The Shadow DOM is a web standard that provides encapsulation for JavaScript, CSS, and templating in web components. It allows developers to create isolated DOM trees within elements, separate from the main document DOM. This encapsulation prevents styles and scripts from leaking in or out, ensuring that component internals remain separate from the rest of the page. Shadow DOM enables more modular and maintainable code by reducing naming conflicts and CSS specificity issues. It’s particularly useful for creating reusable custom elements with self-contained styling and behavior. While primarily used in web components, Shadow DOM can also be leveraged in various scenarios to improve code organization and reduce unintended side effects in complex web applications.</p>"
      }
    ]
  },
  {
    "title": "Type Checkers",
    "content": "<p>Type checkers are tools that analyze code to detect and prevent type-related errors without executing the program. They enforce type consistency, helping developers catch mistakes early in the development process. Popular type checkers include TypeScript for JavaScript, Flow for JavaScript, and mypy for Python. These tools add static typing to dynamically typed languages, offering benefits like improved code reliability, better documentation, and enhanced developer tooling support. Type checkers can infer types in many cases and allow for gradual adoption in existing projects. They help prevent common runtime errors, facilitate refactoring, and improve code maintainability. While adding some overhead to the development process, type checkers are widely adopted in large-scale applications for their ability to catch errors before runtime and improve overall code quality.</p>",
    "subtopics": [
      {
        "title": "TypeScript",
        "content": "<p>TypeScript is a strongly-typed, object-oriented programming language that builds upon JavaScript by adding optional static typing and other features. Developed and maintained by Microsoft, it compiles to plain JavaScript, allowing it to run in any environment that supports JavaScript. TypeScript offers enhanced IDE support with better code completion, refactoring, and error detection during development. It introduces concepts like interfaces, generics, and decorators, enabling more robust software architecture. TypeScript is particularly valuable for large-scale applications, as it improves code maintainability and readability. Its type system helps catch errors early in the development process, reducing runtime errors. With its growing ecosystem and adoption in popular frameworks like Angular, TypeScript has become a standard tool in modern web development.</p>"
      }
    ]
  },
  {
    "title": "SSR",
    "content": "<p>Server-side rendering (SSR) is a technique used in web development where web pages are generated on the server and sent to the client as fully rendered HTML. This approach contrasts with client-side rendering, where the browser builds the page using JavaScript. SSR improves initial page load time and search engine optimization (SEO) by providing complete content to crawlers. It’s particularly beneficial for content-heavy sites and applications requiring fast first-page loads. SSR can be implemented with various frameworks like Next.js for React or Nuxt.js for Vue.js. While it can increase server load and complexity, SSR offers advantages in performance perception, especially on slower devices or networks, and can be combined with client-side hydration for dynamic interactivity after initial load.</p>",
    "subtopics": [
      {
        "title": "React",
        "content": "<p>React is an open-source JavaScript library for building user interfaces, primarily for single-page applications. Developed and maintained by Facebook, it allows developers to create reusable UI components that efficiently update and render as data changes. React uses a virtual DOM for performance optimization and supports a unidirectional data flow. Its component-based architecture promotes modularity and reusability. React’s ecosystem includes tools like Redux for state management and React Native for mobile app development. The library’s declarative nature, efficient rendering, and strong community support have made it one of the most popular choices for front-end development in modern web applications.</p>"
      },
      {
        "title": "Next.js",
        "content": "<p>Next.js is a React-based open-source framework for building server-side rendered and statically generated web applications. It provides features like automatic code splitting, optimized performance, and simplified routing out of the box. Next.js supports both static site generation (SSG) and server-side rendering (SSR), allowing developers to choose the most appropriate rendering method for each page. The framework offers built-in CSS support, API routes for backend functionality, and easy deployment options. Next.js is known for its developer-friendly experience, with features like hot module replacement and automatic prefetching. Its ability to create hybrid apps that combine static and server-rendered pages makes it popular for building scalable, SEO-friendly web applications.</p>"
      },
      {
        "title": "Astro",
        "content": "<p>Astro is a modern static site generator (SSG) and web framework designed for building fast, content-focused websites. It allows developers to use multiple frontend frameworks (like React, Vue, or Svelte) within the same project, automatically rendering components to static HTML at build time. Astro’s unique “partial hydration” approach only sends JavaScript to the browser when necessary, resulting in significantly smaller bundle sizes and faster load times. The framework supports file-based routing, markdown content, and built-in optimizations for images and assets. Astro’s component islands architecture enables developers to create interactive components while maintaining the performance benefits of static HTML, making it particularly well-suited for content-rich sites like blogs, documentation, and marketing pages.</p>"
      },
      {
        "title": "react-router",
        "content": "<p>React Router is a popular routing library for React applications that enables dynamic, client-side routing. It allows developers to create single-page applications with multiple views, managing the URL and history of the browser while keeping the UI in sync with the URL. React Router provides a declarative way to define routes, supporting nested routes, route parameters, and programmatic navigation. It offers components like BrowserRouter, Route, and Link to handle routing logic and navigation. The library also supports features such as lazy loading of components, route guards, and custom history management. React Router’s integration with React’s component model makes it a go-to solution for managing navigation and creating complex, multi-view applications in React ecosystems.</p>"
      },
      {
        "title": "Angular",
        "content": "<p>Angular is a popular open-source web application framework developed and maintained by Google. It uses TypeScript, a statically typed superset of JavaScript, to build scalable and efficient single-page applications (SPAs). Angular follows a component-based architecture, where the user interface is composed of reusable, self-contained components. The framework provides features like two-way data binding, dependency injection, and a powerful template syntax, which simplify the development of complex web applications. Angular also includes a comprehensive set of tools for testing, routing, and state management, making it a full-fledged solution for front-end development. Its modular structure and emphasis on best practices make it particularly suitable for large-scale enterprise applications.</p>"
      },
      {
        "title": "Vue.js",
        "content": "<p>Vue.js is a progressive JavaScript framework for building user interfaces. It’s designed to be incrementally adoptable, allowing developers to integrate it into projects gradually. Vue uses a template-based approach with a virtual DOM for efficient rendering. It features a reactive and composable component system, making it easy to organize and reuse code. Vue’s core library focuses on the view layer, but it can be easily extended with official and community-built tools for state management, routing, and build tooling. Known for its gentle learning curve and flexibility, Vue has gained popularity for both small projects and large-scale applications. Its performance, lightweight nature, and comprehensive documentation have contributed to its widespread adoption in the web development community.</p>"
      },
      {
        "title": "Nuxt.js",
        "content": "<p>Nuxt.js is a higher-level framework built on top of Vue.js, designed to create universal or single-page Vue applications. It simplifies the development process by providing a structured directory layout, automatic routing, and server-side rendering capabilities out of the box. Nuxt.js offers features like static site generation, code splitting, and asynchronous data fetching. It supports both client-side and server-side rendering, allowing developers to choose the most appropriate approach for each page. Nuxt.js emphasizes developer experience and performance optimization, making it popular for building scalable, SEO-friendly Vue applications. Its modular architecture and extensive plugin ecosystem enable easy integration of additional functionalities.</p>"
      },
      {
        "title": "Svelte",
        "content": "<p>Svelte is a modern JavaScript framework for building user interfaces that takes a unique approach to web development. Unlike traditional frameworks that do most of their work in the browser, Svelte shifts that work into a compile step that happens when you build your app. It compiles your code to efficient vanilla JavaScript, resulting in smaller bundle sizes and better runtime performance. Svelte uses a component-based architecture and features a simple, intuitive syntax that allows developers to write less code. It includes built-in state management, CSS scoping, and animations. Svelte’s approach eliminates the need for a virtual DOM, leading to faster initial loads and updates. Its simplicity and performance benefits have been gaining it increasing popularity in the front-end development community.</p>"
      },
      {
        "title": "Svelte Kit",
        "content": "<p>SvelteKit is a framework for building web applications using Svelte, a component-based JavaScript framework. It provides a full-stack development experience, handling both server-side and client-side rendering. SvelteKit offers features like file-based routing, code-splitting, and server-side rendering out of the box. It supports both static site generation and server-side rendering, allowing developers to choose the most appropriate approach for each page. SvelteKit emphasizes simplicity and performance, leveraging Svelte’s compile-time approach to generate highly optimized JavaScript. It includes built-in development tools, easy deployment options, and integrates well with various backend services. SvelteKit’s efficient development experience and flexibility make it an attractive option for building modern, performant web applications.</p>"
      }
    ]
  },
  {
    "title": "GraphQL",
    "content": "<p>GraphQL is a query language and runtime for APIs, developed by Facebook. GraphQL’s flexibility and efficiency make it popular for building complex applications, especially those with diverse client requirements. It’s particularly useful for mobile applications where bandwidth efficiency is crucial. While it requires a paradigm shift from REST, many developers and organizations find GraphQL’s benefits outweigh the learning curve, especially for large-scale or rapidly evolving APIs.</p>",
    "subtopics": [
      {
        "title": "Apollo",
        "content": "<p>Apollo GraphQL is a comprehensive platform for building and managing GraphQL-based data layers in modern applications. It provides a set of open-source tools and libraries that simplify the implementation of GraphQL on both the client and server sides. On the client side, Apollo Client offers powerful caching, state management, and data fetching capabilities, integrating seamlessly with various front-end frameworks. On the server side, Apollo Server facilitates the creation of GraphQL APIs, handling queries, mutations, and subscriptions efficiently. The Apollo platform also includes developer tools for schema management, performance monitoring, and API governance. By abstracting away much of the complexity of GraphQL implementation, Apollo enables developers to build faster, more scalable, and more maintainable applications with a unified data graph.</p>"
      },
      {
        "title": "Relay Modern",
        "content": "<p>Relay is a JavaScript framework developed by Facebook for building data-driven React applications. It’s specifically designed to work with GraphQL, providing a declarative approach to fetching and managing data in complex web applications. Relay optimizes data fetching by colocating data requirements with components, enabling efficient updates and minimizing over-fetching. It handles caching, real-time updates, and optimistic UI updates out of the box. Relay’s architecture promotes scalability and performance in large applications by managing data dependencies and reducing network requests. While it has a steeper learning curve compared to simpler data-fetching solutions, Relay offers significant benefits for applications with complex data requirements, especially when used in conjunction with React and GraphQL.</p>"
      }
    ]
  },
  {
    "title": "PWAs",
    "content": "<p>Progressive Web Apps (PWAs) are web applications that use modern web capabilities to deliver an app-like experience to users. They combine the best features of web and native apps, offering reliability, speed, and engagement. PWAs are built using web technologies (HTML, CSS, JavaScript) but provide features typically associated with native apps, such as offline functionality, push notifications, and home screen installation. They are responsive, work across different devices and browsers, and are discoverable through search engines. PWAs use service workers for background processing and caching, enabling faster load times and offline access. This approach allows developers to create cross-platform applications that are both cost-effective to develop and easy to maintain, while providing users with a seamless, app-like experience directly through their web browser.</p>",
    "subtopics": [
      {
        "title": "PRPL Pattern",
        "content": "<p>The PRPL pattern is a web application architecture strategy designed to improve performance, especially on mobile devices. PRPL stands for Push, Render, Pre-cache, and Lazy-load. It focuses on optimizing the initial load time and subsequent navigation speed. The pattern involves pushing critical resources for the initial route, rendering the initial route as quickly as possible, pre-caching remaining routes, and lazy-loading other routes and non-critical assets. This approach aims to deliver a near-instant loading experience for users, particularly on slower networks and less powerful devices. PRPL is often implemented using modern web technologies like service workers and is commonly associated with Progressive Web Apps (PWAs), though it can be applied to various web application architectures.</p>"
      },
      {
        "title": "RAIL Model",
        "content": "<p>The RAIL Model is a user-centric performance model developed by Google that focuses on improving web application responsiveness and user experience. RAIL stands for Response, Animation, Idle, and Load. It provides specific performance goals: Responses to user input should occur within 100ms; Animations should run at 60 frames per second (16ms per frame); Idle time should be used to complete deferred work; and Load time for interactive content should be under 5 seconds. The model emphasizes the importance of perceived performance, encouraging developers to prioritize user interactions and break up long tasks. By adhering to RAIL guidelines, developers can create web applications that feel fast and responsive, enhancing user satisfaction and engagement.</p>"
      },
      {
        "title": "Performance Metrics",
        "content": "<p>Web performance metrics are quantitative measures of the performance of a web page or application. They are used to assess the speed and efficiency of a web page, and they can help identify areas for improvement. Some common web performance metrics include:</p>"
      },
      {
        "title": "Using Lighthouse",
        "content": "<p>Lighthouse is an open-source tool developed by Google that is used to audit the performance, accessibility, and SEO of web pages. It is available as a browser extension and as a command-line tool, and it can be run on any web page to generate a report with recommendations for improvement. Lighthouse works by simulating the load and interaction of a web page and measuring various performance metrics, such as load time, time to first paint, and time to interactive. It also checks for common issues such as incorrect image sizes, missing alt text, and broken links. Lighthouse provides a comprehensive and easy-to-use tool for identifying and fixing performance and accessibility issues on web pages. It is widely used by web developers and is integrated into many popular development tools.</p>"
      },
      {
        "title": "Using DevTools",
        "content": "<p>Browser Developer Tools, commonly known as DevTools, are built-in features in modern web browsers that provide a suite of debugging and development capabilities. These tools allow developers to inspect, edit, and debug HTML, CSS, and JavaScript in real-time on web pages. Key features include:</p>"
      },
      {
        "title": "Storage",
        "content": "<p>The Web Storage API provides mechanisms for storing key-value pairs in a web browser. It includes two storage objects: localStorage and sessionStorage, which allow you to save data on the client side and persist it across multiple browser sessions, respectively. The Web Storage API is designed to be simple and easy to use, and it is widely supported across modern web browsers. It is often used as an alternative to cookies, as it allows for larger amounts of data to be stored and is more efficient in terms of performance.</p>"
      },
      {
        "title": "Web Sockets",
        "content": "<p>Web Sockets is a technology that allows for full-duplex communication over a single TCP connection. It enables real-time, bi-directional communication between a client and a server, and is typically used in applications that require high-speed, low-latency communication, such as online gaming and real-time data streaming. Web Sockets utilizes a persistent connection between a client and a server, allowing for continuous data exchange without the need for the client to send additional requests to the server. This makes it more efficient and faster than other technologies, such as HTTP, which require a new request to be sent for each piece of data. Web Sockets is supported by most modern web browsers and can be used with a variety of programming languages and frameworks.</p>"
      },
      {
        "title": "Server Sent Events",
        "content": "<p>Server-Sent Events (SSE) is a technology that allows a web server to push data to a client in real-time. It uses an HTTP connection to send a stream of data from the server to the client, and the client can listen for these events and take action when they are received. SSE is useful for applications that require real-time updates, such as chat systems, stock tickers, and social media feeds. It is a simple and efficient way to establish a long-lived connection between a client and a server, and it is supported by most modern web browsers.</p>"
      },
      {
        "title": "Service Workers",
        "content": "<p>Service Workers are a type of web worker that acts as a proxy between a web page and the network, allowing web developers to build offline-first and reliable applications. Service Workers can intercept network requests, access the cache, and make decisions on how to respond to a request based on the available resources. Service Workers are written in JavaScript and are registered by a web page. Once registered, they can control the page and all its requests, even when the page is not open in a browser. This allows Service Workers to enable features such as push notifications, background synchronization, and offline support. Service Workers are supported by most modern web browsers, and they are an essential component of progressive web applications (PWAs).</p>"
      },
      {
        "title": "Location",
        "content": "<p>The Geolocation API is a web API that provides access to the device’s location data, such as latitude and longitude. It allows web developers to build location-based applications, such as mapping and location sharing, by using the device’s GPS, Wi-Fi, and other sensors to determine the user’s location. To use the Geolocation API, a web page must first request permission from the user to access their location. If permission is granted, the page can then use the <code>navigator.geolocation</code> object to access the device’s location data. The API provides several methods for getting the user’s current location, watching for location changes, and calculating distances between two locations.</p>"
      },
      {
        "title": "Notifications",
        "content": "<p>The Notifications API is a web API that allows web pages to display system-level notifications to the user. These notifications can be used to alert the user of important events, such as new messages or updates, even when the web page is not open in the browser. To use the Notifications API, a web page must first request permission from the user to display notifications. If permission is granted, the page can then use the <code>Notification</code> constructor to create a new notification and display it to the user. The notification can include a title, body text, and an icon, and it can be customized with options such as a timeout and a click action.</p>"
      },
      {
        "title": "Device Orientation",
        "content": "<p>The Device Orientation API is a web API that provides access to the device’s orientation and motion data, such as its pitch, roll, and yaw. It allows web developers to build applications that can respond to the device’s orientation and motion, such as augmented reality and motion-controlled games. To use the Device Orientation API, a web page must first request permission from the user to access the device’s orientation data. If permission is granted, the page can then use the DeviceOrientationEvent object to access the device’s orientation data and respond to changes in orientation. The API provides several properties for accessing the device’s orientation and motion data, as well as events for detecting changes in orientation.</p>"
      },
      {
        "title": "Payments",
        "content": "<p>The Payment Request API is a web API that allows web developers to build checkout flows within their web applications. It provides a standardized, browser-based interface for collecting payment and shipping information from the user, and it supports a wide range of payment methods, including credit cards, debit cards, and digital wallets. To use the Payment Request API, a web page must first create a <code>PaymentRequest</code> object and specify the payment and shipping options that are available to the user. The page can then invoke the Payment Request UI by calling the <code>show()</code> method on the <code>PaymentRequest</code> object. The user can then select their preferred payment and shipping options and confirm the payment, at which point the Payment Request API will return a payment response object that can be used to complete the transaction.</p>"
      },
      {
        "title": "Credentials",
        "content": "<p>The Credential Management API is a web standard that allows websites to interact with the browser’s credential manager to store, retrieve, and manage user credentials. It provides a programmatic interface for seamless and secure user authentication, enabling features like automatic sign-in and one-tap sign-up. The API supports various credential types, including passwords, federated identities, and public key credentials. By leveraging this API, developers can improve user experience by reducing login friction, implementing smoother account switching, and enhancing overall security. It works in conjunction with password managers and platform authenticators, helping to streamline authentication processes across devices and browsers while adhering to modern security practices.</p>"
      }
    ]
  },
  {
    "title": "Static Site Generators",
    "content": "<p>Static site generators (SSGs) are tools that create HTML websites from raw data and templates, producing pre-rendered pages at build time rather than at runtime. They combine the benefits of static websites (speed, security, simplicity) with the flexibility of dynamic sites. SSGs typically use markup languages like Markdown for content, templating engines for layouts, and generate a fully static website that can be hosted on simple web servers or content delivery networks. Popular SSGs include Jekyll, Hugo, Gatsby, and Eleventy. They’re well-suited for blogs, documentation sites, and content-focused websites. SSGs offer advantages in performance, version control integration, and reduced server-side complexity, making them increasingly popular for a wide range of web projects.</p>",
    "subtopics": [
      {
        "title": "Next.js",
        "content": "<p>Next.js is a React-based open-source framework for building server-side rendered and statically generated web applications. It provides features like automatic code splitting, optimized performance, and simplified routing out of the box. Next.js supports both static site generation (SSG) and server-side rendering (SSR), allowing developers to choose the most appropriate rendering method for each page. The framework offers built-in CSS support, API routes for backend functionality, and easy deployment options. Next.js is known for its developer-friendly experience, with features like hot module replacement and automatic prefetching. Its ability to create hybrid apps that combine static and server-rendered pages makes it popular for building scalable, SEO-friendly web applications.</p>"
      },
      {
        "title": "Astro",
        "content": "<p>Astro is a modern static site generator (SSG) and web framework designed for building fast, content-focused websites. It allows developers to use multiple frontend frameworks (like React, Vue, or Svelte) within the same project, automatically rendering components to static HTML at build time. Astro’s unique “partial hydration” approach only sends JavaScript to the browser when necessary, resulting in significantly smaller bundle sizes and faster load times. The framework supports file-based routing, markdown content, and built-in optimizations for images and assets. Astro’s component islands architecture enables developers to create interactive components while maintaining the performance benefits of static HTML, making it particularly well-suited for content-rich sites like blogs, documentation, and marketing pages.</p>"
      },
      {
        "title": "Vuepress",
        "content": "<p>VuePress is a static site generator powered by Vue.js, primarily designed for creating documentation websites. It generates pre-rendered static HTML for each page, resulting in fast loading times and SEO-friendly content. VuePress features a Vue-powered theming system, automatic code syntax highlighting, and a default theme optimized for technical documentation. It supports markdown content with Vue components, allowing for dynamic and interactive documentation. VuePress offers built-in search functionality, responsive layouts, and easy customization through plugins and themes. While primarily used for documentation, it’s versatile enough for blogs and simple websites. VuePress’s combination of simplicity, performance, and Vue.js integration makes it popular for creating modern, fast-loading documentation sites and technical blogs.</p>"
      },
      {
        "title": "Eleventy",
        "content": "<p>Eleventy (11ty) is a simple to use, easy to customize, highly performant and powerful static site generator with a helpful set of plugins (e.g. navigation, build-time image transformations, cache assets). Pages can be built and written with a variety of template languages (HTML, Markdown, JavaScript, Liquid, Nunjucks, Handlebars, Mustache, EJS, Haml, Pug or JS template literals). But it also offers the possibility to dynamically create pages from local data or external sources that are compiled at build time. It has zero client-side JavaScript dependencies.</p>"
      },
      {
        "title": "Nuxt.js",
        "content": "<p>Nuxt.js is a higher-level framework built on top of Vue.js, designed to create universal or single-page Vue applications. It simplifies the development process by providing a structured directory layout, automatic routing, and server-side rendering capabilities out of the box. Nuxt.js offers features like static site generation, code splitting, and asynchronous data fetching. It supports both client-side and server-side rendering, allowing developers to choose the most appropriate approach for each page. Nuxt.js emphasizes developer experience and performance optimization, making it popular for building scalable, SEO-friendly Vue applications. Its modular architecture and extensive plugin ecosystem enable easy integration of additional functionalities.</p>"
      }
    ]
  },
  {
    "title": "Mobile Apps",
    "content": "<p>Mobile applications are software programs designed to run on mobile devices such as smartphones and tablets. They are typically distributed through app stores like Google Play or Apple’s App Store. Mobile apps can be native (built specifically for one platform using languages like Swift for iOS or Kotlin for Android), hybrid (web technologies wrapped in a native container), or cross-platform (using frameworks like React Native or Flutter). These apps leverage device-specific features such as GPS, cameras, and sensors to provide rich, interactive experiences. They cover a wide range of functions from productivity and entertainment to social networking and e-commerce. Mobile app development considers factors like user interface design, performance optimization, offline functionality, and security to ensure a smooth user experience across various devices and operating systems.</p>",
    "subtopics": [
      {
        "title": "React Native",
        "content": "<p>React Native is an open-source mobile application development framework created by Facebook. It allows developers to build native mobile apps for iOS and Android using JavaScript and React. React Native translates JavaScript code into native components, providing near-native performance and a genuine native user interface. It enables code reuse across platforms, speeding up development and reducing costs. The framework offers hot reloading for quick iterations, access to native APIs, and a large ecosystem of third-party plugins. React Native’s “learn once, write anywhere” philosophy and its ability to bridge web and mobile development make it popular for creating cross-platform mobile applications, especially among teams already familiar with React for web development.</p>"
      },
      {
        "title": "Flutter",
        "content": "<p>Flutter is an open-source UI software development kit created by Google for building natively compiled, multi-platform applications from a single codebase. It uses the Dart programming language and provides a rich set of pre-designed widgets for creating responsive and visually appealing user interfaces. Flutter’s architecture allows for fast development with hot reload, enabling developers to see changes instantly. It supports iOS, Android, web, and desktop platforms, offering true cross-platform development. Flutter uses a custom rendering engine, Skia, to draw UI components, ensuring consistent appearance across devices. While known for mobile app development, Flutter’s expanding ecosystem and performance improvements have increased its adoption for web and desktop applications as well.</p>"
      },
      {
        "title": "Ionic",
        "content": "<p>Ionic is an open-source UI toolkit for building high-quality, cross-platform mobile and desktop applications using web technologies (HTML, CSS, and JavaScript). It leverages popular web frameworks like Angular, React, or Vue.js for application logic, while providing a rich set of pre-built UI components and native device functionalities. Ionic uses Cordova or Capacitor to wrap web apps for native deployment, allowing developers to create hybrid apps that can access device features through plugins. The framework emphasizes performance and native look-and-feel, offering adaptive styling for different platforms. With its focus on web standards and cross-platform compatibility, Ionic enables developers to maintain a single codebase for multiple platforms, making it a popular choice for rapid mobile app development.</p>"
      }
    ]
  },
  {
    "title": "Desktop Apps",
    "content": "<p>Desktop applications applications typically use frameworks like Electron, NW.js (Node-WebKit), or Tauri, which combine a JavaScript runtime with a native GUI toolkit. This approach allows developers to use their web development skills to create cross-platform desktop apps. Electron, developed by GitHub, is particularly popular, powering applications like Visual Studio Code, Atom, and Discord. These frameworks provide APIs to access native system features, enabling JavaScript to interact with the file system, system tray, and other OS-specific functionalities. While offering rapid development and cross-platform compatibility, JavaScript desktop apps can face challenges in terms of performance and resource usage compared to traditional native applications. However, they benefit from the vast ecosystem of JavaScript libraries and tools, making them an attractive option for many developers and businesses.</p>",
    "subtopics": [
      {
        "title": "Tauri",
        "content": "<p>Tauri is an open-source framework for building lightweight, secure desktop applications using web technologies. It allows developers to create cross-platform apps with HTML, CSS, and JavaScript, while using a Rust backend for core functionality. Tauri offers smaller bundle sizes compared to Electron, as it leverages the operating system’s native webview instead of bundling Chromium. It provides robust security features, including a custom protocol for IPC (Inter-Process Communication) and fine-grained permissions. Tauri supports multiple JavaScript frameworks and offers API bindings for various system-level operations. Its emphasis on performance, security, and small binary sizes makes it an attractive option for developers seeking to create efficient desktop applications with web technologies.</p>"
      },
      {
        "title": "Electron",
        "content": "<p>Electron is an open-source framework developed by GitHub that enables developers to build cross-platform desktop applications using web technologies. It combines the Chromium rendering engine with the Node.js runtime, allowing applications to be written in HTML, CSS, and JavaScript. Electron provides APIs to access native operating system functions, bridging the gap between web and desktop development. It’s widely used for creating popular applications like Visual Studio Code, Atom, and Discord. Electron apps benefit from rapid development cycles, cross-platform compatibility, and access to a vast ecosystem of web technologies and Node.js modules. However, they can face challenges with resource usage and performance compared to native applications. Despite these trade-offs, Electron remains a popular choice for developers seeking to leverage web skills for desktop app development.</p>"
      },
      {
        "title": "Flutter",
        "content": "<p>Flutter is an open-source UI software development kit created by Google for building natively compiled, multi-platform applications from a single codebase. It uses the Dart programming language and provides a rich set of pre-designed widgets for creating responsive and visually appealing user interfaces. Flutter’s architecture allows for fast development with hot reload, enabling developers to see changes instantly. It supports iOS, Android, web, and desktop platforms, offering true cross-platform development. Flutter uses a custom rendering engine, Skia, to draw UI components, ensuring consistent appearance across devices. While known for mobile app development, Flutter’s expanding ecosystem and performance improvements have increased its adoption for web and desktop applications as well.</p>"
      }
    ]
  }
]
```

---
transition: fade-out
---

# Pengumpulan Data
Penyimpanan ke Database (Tabel `topics`)
|id|title|content|type|
|---|---|---|---|
|14|Design and Development Principles|<p>Design and Development Principles are fundamental guidelines that inform the creation of software systems. Key principles include:</p>|backend|
|38|Web Security Basics|<p>Web security knowledge encompasses understanding and implementing practices to protect websites, web applications, and web services from various cyber threats. Key areas include:</p>|frontend|

---
transition: fade-out
---
# Pengumpulan Data
Penyimpanan ke Database (Tabel `subtopics`)

|id|topic_id|title|content|
|---|---|---|---|
|171|39|Shadow DOM|<p>The Shadow DOM is a web standard that provides encapsulation for JavaScript, CSS, and templating in web components. It allows developers to create isolated DOM trees within elements, separate from the main document DOM. This encapsulation prevents styles and scripts from leaking in or out, ensuring that component internals remain separate from the rest of the page. Shadow DOM enables more modular and maintainable code by reducing naming conflicts and CSS specificity issues. It’s particularly useful for creating reusable custom elements with self-contained styling and behavior. While primarily used in web components, Shadow DOM can also be leveraged in various scenarios to improve code organization and reduce unintended side effects in complex</p>|
---
transition: fade-out
---

# Pengumpulan Data
Udemy API

```js {1-2|4-14|16|18-31|33-45|47-55|57}
const MongoClient = require('mongodb').MongoClient
const url = 'mongodb://localhost:27017'

let subs = [
    "Programming Languages",
    "Software Testing",
    "Software Development Tools",
    "Web Development",
    "Database Design & Development",
    "Software Engineering",
    "Network & Security",
    "Other IT & Software",
    "Operating Systems & Servers",
]

let id = 1

const fetchData = async (url) => {
    try {
        const res = await fetch(url, {
            headers: {
                'Authorization': 'Basic SjdJRFRra1FmbkQxNGFWVUlPTTB5aDFsOGhRTmszemxVMG01UWRsMjozRmxXZkQ0aHA1N2lvbDhidnhiN3ZhcXNlc1U5d0NScENWM1FhN2FMT1RpUmdHSFFJb0Z0bWprZlhFaThuRWkxdXp6RUc5dHBhR0NhRGVaVUFKODVVSmhKakh1ZVo5NEpoY21IdG1IRGdmbEFsNGJyYkxwQ3JYcDl5ZjZ1c0VSRA=='
            }})
        if (!res.ok) {
            throw new Error('Failed to fetch data')
        }
        return await res.json()
    } catch (error) {
        throw error
    }
}

const saveToDB = async (data) => {
    const client = new MongoClient(url)
    try {
        await client.connect()
        const db = client.db('course_compass')
        const res = await db.collection('meta').insertOne(data)
        console.log(data.subcategory + ' meta inserted')
    } catch (error) {
        throw error
    } finally {
        await client.close()
    }
}

const fetchMeta = async (sub) => {
    const uri = `https://www.udemy.com/api-2.0/courses/?fields[course]=id&language=en&subcategory=${sub.replace('&', '%26')}&page=1&page_size=1`
    const data = await fetchData(uri)
    await saveToDB({
        _id: id++,
        subcategory: sub,
        total: data.count,
    })
}

subs.forEach(sub => fetchMeta(sub))
```

---
transition: fade-out
---

# Pengumpulan Data
Udemy API

```json
[
  {
    "_id": 1,
    "subcategory": "Network & Security",
    "total": 3703
  },
  {
    "_id": 2,
    "subcategory": "Programming Languages",
    "total": 4173
  },
  {
    "_id": 3,
    "subcategory": "Software Testing",
    "total": 887
  },
  {
    "_id": 4,
    "subcategory": "Operating Systems & Servers",
    "total": 1305
  },
  {
    "_id": 5,
    "subcategory": "Other IT & Software",
    "total": 8958
  },
  {
    "_id": 6,
    "subcategory": "Software Engineering",
    "total": 1222
  },
  {
    "_id": 7,
    "subcategory": "Web Development",
    "total": 6396
  },
  {
    "_id": 8,
    "subcategory": "Database Design & Development",
    "total": 1155
  },
  {
    "_id": 9,
    "subcategory": "Software Development Tools",
    "total": 928
  }
]
```

---
transition: fade-out
---

# Pengumpulan Data
Udemy API

```js {1-2|6-18|20-44|46-58|60-86|88-107}
const { MongoClient } = require('mongodb');
const retry = require('retry');

(async () => {

const PQueue = (await import('p-queue')).default;

const url = 'mongodb://localhost:27017';

const retryOptions = {
    retries: 5,  // Number of attempts before falling back to another retry method
    factor: 1.25,
    minTimeout: 1 * 1000,
    maxTimeout: 100 * 1000,
};

const maxConcurrency = 5; // Maximum number of concurrent fetch operations
const queue = new PQueue({ concurrency: maxConcurrency });

const fetchData = async (url) => {
    const operation = retry.operation(retryOptions);

    return new Promise((resolve, reject) => {
        operation.attempt(async () => {
            try {
                const res = await fetch(url, {
                    headers: {
                        'Authorization': 'Basic SjdJRFRra1FmbkQxNGFWVUlPTTB5aDFsOGhRTmszemxVMG01UWRsMjozRmxXZkQ0aHA1N2lvbDhidnhiN3ZhcXNlc1U5d0NScENWM1FhN2FMT1RpUmdHSFFJb0Z0bWprZlhFaThuRWkxdXp6RUc5dHBhR0NhRGVaVUFKODVVSmhKakh1ZVo5NEpoY21IdG1IRGdmbEFsNGJyYkxwQ3JYcDl5ZjZ1c0VSRA=='
                    }
                });
                if (!res.ok) {
                    throw new Error('Failed to fetch data');
                }
                const data = await res.json();
                resolve(data);
            } catch (error) {
                if (operation.retry(error)) {
                    return;
                }
                reject(error);
            }
        });
    });
};

const saveToDB = async (data) => {
    const client = new MongoClient(url);
    try {
        await client.connect();
        const db = client.db('course_compass');
        const res = await db.collection('courses').insertMany(data, { ordered: false }); // Use ordered:false to continue inserting even if duplicates are present
        console.log(res.insertedCount + ' courses inserted');
    } catch (error) {
        throw error;
    } finally {
        await client.close();
    }
};

const fetchCourses = async (sub, page) => {
    const uri = `https://www.udemy.com/api-2.0/courses/?fields[course]=@all&language=en&subcategory=${encodeURIComponent(sub)}&page=${page}&page_size=99`;

    const operation = retry.operation(retryOptions);
    operation.attempt(async (currentAttempt) => {
        try {
            const data = await fetchData(uri);

            const insert = data.results.map(course => {
                course._id = course.id;
                delete course.id;
                return course;
            });

            await saveToDB(insert);
            console.log('Fetched ' + data.results.length + ' courses in ' + sub);
        } catch (error) {
            if (currentAttempt >= retryOptions.retries) {
                console.error('Maximum retries reached for ' + sub + ' page ' + page);
            } else if (operation.retry(error)) {
                console.error('Retrying, attempt:', currentAttempt);
            } else {
                console.error('Failed to fetch courses in ' + sub);
            }
        }
    });
};

const main = async () => {
    const client = new MongoClient(url);
    try {
        await client.connect();
        const db = client.db('course_compass');
        const metas = await db.collection('meta').find().toArray();

        metas.forEach(meta => {
            const page_size = 99;
            const pages = Math.ceil(meta.total / page_size);
            for (let i = 1; i <= pages; i++) {
                queue.add(() => fetchCourses(meta.subcategory, i));
            }
        });
    } catch (error) {
        console.error('Failed to connect to the database:', error);
    } finally {
        await client.close();
    }
};

main();
})()
```

---
transition: fade-out
---

# Pengumpulan Data
Udemy API

```json
[{
  "_id": 381082,
  "_class": "course",
  "title": "Security Awareness Campaigns (Lite)",
  "url": "/course/security-awareness-campaigns/",
  "is_paid": false,
  "price": "Free",
  "price_detail": null,
  "price_serve_tracking_id": "4LCN4-qXTK6A7bZaDDuWuw",
  "visible_instructors": [
    {
      "_class": "user",
      "title": "Michael Goedeker",
      "name": "Michael",
      "display_name": "Michael Goedeker",
      "job_title": "Cyber Security Researcher, Author, Trainer, M.Sc. CISSP",
      "image_50x50": "https://img-c.udemycdn.com/user/50x50/8980244_c9c3_2.jpg",
      "image_100x100": "https://img-c.udemycdn.com/user/100x100/8980244_c9c3_2.jpg",
      "initials": "MG",
      "url": "/user/michaelgoedeker2/"
    }
  ],
  "image_125_H": "https://img-c.udemycdn.com/course/125_H/381082_8049_6.jpg",
  "image_240x135": "https://img-c.udemycdn.com/course/240x135/381082_8049_6.jpg",
  "is_practice_test_course": false,
  "image_480x270": "https://img-c.udemycdn.com/course/480x270/381082_8049_6.jpg",
  "published_title": "security-awareness-campaigns",
  "tracking_id": "",
  "locale": {
    "_class": "locale",
    "locale": "en_US",
    "title": "English (US)",
    "english_title": "English (US)",
    "simple_english_title": "English"
  },
  "description": "<p>  \t        Security Awareness Campaigns is about the components and reality of what makes awareness campaigns successful and which components are needed in it. This course will cover the basics of a security awareness campaign that is aimed at increasing security levels by addressing social engineering attacks and communicating the basics of awareness and threats companies face today.  </p>  <p>  \t<strong style=\"\">Learn the basic concepts of security awareness campaigns, quickly and easily!</strong>  </p>  <p>  \t    This course goes through relevant research into successful and failed attempts at increasing awareness, also going through complex standards and making them simple and easy to understand.  </p>  <p>  \t    The full version gives you research, tips and information you need to be successful in creating your own security awareness campaign.  </p>  <p>  \t<strong style=\"\">  There are over 22 lectures in the full version that cover:  </strong>  </p>  <ul style=\"\">  \t<li>Introduction to security awareness campaigns</li>  \t<li>What components are needed</li>  \t<li>Security Drivers</li>  \t<li>Vulnerabilities that companies face</li>  \t<li>Business value of campaigns</li>  \t<li>Components of the awareness campaign</li>  \t<li>Security Policy</li>  \t<li>Laptop and Desktop</li>  \t<li>Mobile Devices</li>  \t<li>Data Security and Encryption</li>  \t<li>Incident Response</li>  \t<li>Change Management</li>  \t<li>Security Organization</li>  \t<li>How awareness mitigates risks</li>  \t<li>Practical examples of how awareness has stopped attacks in reality</li>  </ul>  <p>  \t    This course goes through materials and actual projects and gives you the simple scoop on how to create great awareness campaigns that work and which elements you can use in your awareness campaign. It also goes through information that is also important for everyone to know, even if you do not create an awareness campaign, it will help you understand basic concepts.  </p>",
  "headline": "This is the \"lite\" version of Security Awareness Campaigns and is meant to give you an idea of the full course.",
  "num_subscribers": 48269,
  "caption_locales": [
    {
      "_class": "locale",
      "locale": "en_US",
      "title": "English (US)",
      "english_title": "English (US)"
    }
  ],
  "discount": null,
  "discount_price": null,
  "avg_rating": 4.255102,
  "avg_rating_recent": 4.27604,
  "rating": 4.27604,
  "num_reviews": 5733,
  "num_reviews_recent": 51,
  "rating_distribution": [
    {
      "rating": 1,
      "count": 48
    },
    {
      "rating": 2,
      "count": 115
    },
    {
      "rating": 3,
      "count": 992
    },
    {
      "rating": 4,
      "count": 2734
    },
    {
      "rating": 5,
      "count": 1844
    }
  ],
  "favorite_time": null,
  "archive_time": null,
  "earnings": "$0.00",
  "completion_ratio": 0,
  "is_wishlisted": false,
  "num_quizzes": 0,
  "num_lectures": 8,
  "num_published_lectures": 8,
  "num_published_quizzes": 0,
  "num_curriculum_items": 8,
  "num_of_published_curriculum_objects": 8,
  "num_cpe_credits": null,
  "is_private": false,
  "num_practice_tests": 0,
  "num_published_practice_tests": 0,
  "original_price_text": "Free",
  "quality_status": "approved",
  "status_label": "Live",
  "can_edit": false,
  "features": {
    "_class": "course",
    "discussions_create": true,
    "discussions_view": true,
    "discussions_replies_create": true,
    "enroll": true,
    "reviews_create": true,
    "reviews_view": true,
    "reviews_responses_create": true,
    "announcements_comments_view": true,
    "educational_announcements_create": true,
    "promotional_announcements_create": true,
    "promotions_create": true,
    "promotions_view": true,
    "students_view": true
  },
  "gift_url": "https://www.udemy.com/gift/security-awareness-campaigns/",
  "num_invitation_requests": 0,
  "notification_settings": {},
  "is_banned": false,
  "is_published": true,
  "intended_category": null,
  "image_48x27": "https://img-c.udemycdn.com/course/48x27/381082_8049_6.jpg",
  "image_50x50": "https://img-c.udemycdn.com/course/50x50/381082_8049_6.jpg",
  "image_75x75": "https://img-c.udemycdn.com/course/75x75/381082_8049_6.jpg",
  "image_96x54": "https://img-c.udemycdn.com/course/96x54/381082_8049_6.jpg",
  "image_100x100": "https://img-c.udemycdn.com/course/100x100/381082_8049_6.jpg",
  "image_200_H": "https://img-c.udemycdn.com/course/200_H/381082_8049_6.jpg",
  "image_304x171": "https://img-c.udemycdn.com/course/304x171/381082_8049_6.jpg",
  "image_750x422": "https://img-c.udemycdn.com/course/750x422/381082_8049_6.jpg",
  "has_certificate": false,
  "primary_category": {
    "id": 294,
    "title": "IT & Software",
    "title_cleaned": "it-and-software",
    "url": "/courses/it-and-software/",
    "icon_class": "udi udi-it-and-software",
    "type": "category",
    "channel_id": null,
    "_class": "course_category"
  },
  "primary_subcategory": {
    "id": 134,
    "title": "Network & Security",
    "title_cleaned": "network-and-security",
    "url": "/courses/it-and-software/network-and-security/",
    "icon_class": "udi udi-it-and-software",
    "type": "subcategory",
    "channel_id": null,
    "_class": "course_subcategory"
  },
  "is_enrollable_on_mobile": true,
  "is_in_any_ufb_content_collection": false,
  "is_in_user_subscription": false,
  "is_in_subscribed_content_collections": false,
  "has_closed_caption": true,
  "caption_languages": [
    "English [Auto]"
  ],
  "created": "2014-12-30T19:28:49Z",
  "instructional_level": "Beginner Level",
  "instructional_level_simple": "Beginner",
  "estimated_content_length": 33,
  "content_info": "33 total mins",
  "content_info_short": "33 mins",
  "content_length_practice_test_questions": 0,
  "requirements_data": {
    "items": [
      "Just bring your passion for technology and learning how to take security into your own hands"
    ]
  },
  "what_you_will_learn_data": {
    "items": [
      "Lite version of Security Awareness Campaigns training",
      "Basic Security Aspects covered in an awareness campaign"
    ]
  },
  "who_should_attend_data": {
    "items": [
      "Everyone interested in increasing security and privacy of information",
      "Anyone interested in understanding why security awareness is important"
    ]
  },
  "is_available_on_google_app": true,
  "organization_id": null,
  "google_in_app_purchase_price_text": null,
  "promo_asset": {
    "_class": "asset",
    "id": 2455474,
    "asset_type": "Video",
    "title": "Security Awareness Campaigns_Intro.mp4",
    "title_cleaned": "securityawarenesscampaignsintromp4",
    "description": "",
    "length": 89,
    "status": 1,
    "download_urls": {
      "Video": [
        {
          "type": "video/mp4",
          "label": "720",
          "file": "https://mp4-c.udemycdn.com/2015-01-07_02-32-47-7fb6a22157d772d23d20e899771babfb/WebHD_720p.mp4?Expires=1720192474&Signature=8CLQFhD-SXvH~MPW8WbB7-27xUyHOk4h2YyP-zni1lQUwXZb9~DI3xvv-Jrh8VIpYFm1WeMtitDtlB6ICg8zAsQVH6Dgn8j1pQH7ahZBuZTNB3yND4vpEoTJbknp55JQyzxhMXn~9Z90OGDa1zFDEGB4NuSRjqSqIQPvMy6eQMNkKnWFgY9PadiqJL-7kYZR4BoH913fFSBw7cSFPcXPrLOofK4QE8VWBWEt9BzaQgsAu6TOBc3NJfh~OdymxXno5a3FvcdJIu5Cz8aw-F~XXFTmaW89sXtBh0w5cm24pEWZmAOruYN0vQW3-~QL8Daz1AoFCz-lGF6iLdljdw068A__&Key-Pair-Id=K3MG148K9RIRF4"
        },
        {
          "type": "video/mp4",
          "label": "360",
          "file": "https://mp4-c.udemycdn.com/2015-01-07_02-32-47-7fb6a22157d772d23d20e899771babfb/WebHD.mp4?Expires=1720192474&Signature=gw31xCW2k4R~3YS7BgPYUVb1MlLRrm4p20cBAG4YsgEYiH21W~uVmYYXD4M3uKeAuoAOg87UxQDWQyyU05GvfDE-t3XvnXlMOSbKpo3Mpwv9tmCK~mrP~PawUWyO09uya3m4rkmtloVy7aZpK5soWQTIWyGwr0fYV0ivS4LmCdP6musLHzg1d1j4cSX9HtcJ3iWyRfPBJ-mZgiyQpZONGlzzBCcx9apHgNCjKGCYXkvjgVU1LaPrd~IZh9mUSLNE~3HZtEloj-X4UB035r2bdUaCb~BAI~aE6qsUAmclLEj50Xm4BwA58q7x49vZ3E8LBwkV0ysVwIJoq9Q5lMkaOg__&Key-Pair-Id=K3MG148K9RIRF4"
        }
      ]
    }
  },
  "is_user_subscribed": false,
  "apple_in_app_product_id": null,
  "is_available_on_ios": true,
  "google_in_app_product_id": null,
  "faq": [
    {
      "question": "How long do I have access to the course materials?",
      "answer": "You can view and review the lecture materials indefinitely, like an on-demand channel."
    },
    {
      "question": "Can I take my courses with me wherever I go?",
      "answer": "Definitely! If you have an internet connection, courses on Udemy are available on any device at any time. If you don't have an internet connection, some instructors also let their students download course lectures. That's up to the instructor though, so make sure you get on their good side!"
    }
  ],
  "apple_in_app_purchase_price_text": null,
  "type_label": "course",
  "google_in_app_price_detail": null,
  "apple_in_app_price_detail": null,
  "quality_review_process": {
    "_class": "quality_review_process",
    "id": 3030,
    "status": "approved",
    "score": 50,
    "admin_rating": 7
  },
  "is_organization_only": false,
  "is_cpe_compliant": false,
  "cpe_field_of_study": null,
  "cpe_program_level": null,
  "was_ever_published": true,
  "buyable_object_type": "course",
  "published_time": "2015-01-05T00:53:30Z",
  "is_marketing_boost_agreed": true,
  "is_owned_by_instructor_team": false,
  "is_owner_terms_banned": false,
  "is_taking_disabled": false,
  "content_length_video": 1589,
  "checkout_url": "/payment/checkout/express/course/381082/",
  "prerequisites": [
    "Just bring your passion for technology and learning how to take security into your own hands"
  ],
  "objectives": [
    "Lite version of Security Awareness Campaigns training",
    "Basic Security Aspects covered in an awareness campaign"
  ],
  "objectives_summary": [
    "Lite version of Security Awareness Campaigns training",
    "Basic Security Aspects covered in an awareness campaign"
  ],
  "target_audiences": [
    "Everyone interested in increasing security and privacy of information",
    "Anyone interested in understanding why security awareness is important"
  ],
  "last_accessed_time": null,
  "enrollment_time": null,
  "course_has_labels": [
    {
      "_class": "course_has_label",
      "id": 90654,
      "label": {
        "_class": "course_label",
        "id": 5316,
        "title": "Cyber Security",
        "url": "/topic/cyber-security/",
        "icon_class": "udi udi-line-star",
        "type": "topic",
        "display_name": "Cyber Security"
      },
      "is_primary": true
    }
  ],
  "bestseller_badge_content": null,
  "badges": [],
  "free_course_subscribe_url": "/course/subscribe/?courseId=381082",
  "is_recently_published": false,
  "last_update_date": "2015-01-07",
  "num_article_assets": 0,
  "num_coding_exercises": 0,
  "num_assignments": 0,
  "num_additional_assets": 0,
  "preview_url": "/course/381082/preview/",
  "landing_preview_as_guest_url": "/course/security-awareness-campaigns/?instructorPreviewMode=guest",
  "context_info": {
    "category": {
      "id": 294,
      "title": "IT & Software",
      "url": "/courses/it-and-software/",
      "tracking_object_type": "cat"
    },
    "subcategory": null,
    "label": {
      "id": 5316,
      "display_name": "Cyber Security",
      "title": "Cyber Security",
      "topic_channel_url": "/topic/cyber-security/",
      "url": "/topic/cyber-security/",
      "tracking_object_type": "cl"
    }
  },
  "has_sufficient_preview_length": true,
  "has_org_only_setting": false,
  "has_labs_in_course_prompt_setting": false,
  "is_draft": false,
  "custom_category_ids": [],
  "alternate_redirect_course_id": 0,
  "is_approved": true,
  "is_organization_eligible": true,
  "instructor_status": {
    "_class": "instructor_course_status",
    "id": 185116,
    "user": {
      "_class": "user",
      "title": "Michael Goedeker",
      "name": "Michael",
      "display_name": "Michael Goedeker"
    },
    "status": 1,
    "respond_time_frame": "1 week",
    "available_date": null
  },
  "available_features": [],
  "enroll_url": "/course/381082/enroll/",
  "learn_url": "/course/security-awareness-campaigns/learn/",
  "retirement_date": null,
  "is_course_available_in_org": null,
  "is_in_personal_plan_collection": false,
  "is_in_premium": false,
  "is_language_course": false,
  "has_508_closed_captions": false,
  "is_coding_exercises_badge_eligible": false,
  "content_collections": [],
  "is_course_in_ub_ever": false,
  "has_course_a_published_coding_exercise": false,
  "published_lecture_ids": [
    2179026,
    2170568,
    2170570,
    2176496,
    2178700,
    2178882,
    2178586,
    2170556
  ],
  "predictive_score": null,
  "relevancy_score": null,
  "input_features": null,
  "lecture_search_result": null,
  "curriculum_lectures": [],
  "order_in_results": null,
  "curriculum_items": [],
  "instructor_name": null
}]
```

---
transition: fade-out
---

# Pengumpulan Data
Udemy API

```js {1|4-11|14-19|21-41|45-48|50-66|68-69}
const retry = require('retry');

(async () => {
    const { MongoClient } = await import('mongodb');
    const PQueue = (await import('p-queue')).default;

    const url = 'mongodb://localhost:27017';
    const client = new MongoClient(url);

    const concurrencyLimit = 5; // Batasi jumlah permintaan simultan
    const queue = new PQueue({ concurrency: concurrencyLimit });

    const fetchData = async (url) => {
        const operation = retry.operation({
            retries: 5,
            factor: 1.25,
            minTimeout: 1 * 1000,
            maxTimeout: 100 * 1000,
        });

        return new Promise((resolve, reject) => {
            operation.attempt(async () => {
                try {
                    const res = await fetch(url, {
                        headers: {
                            'Authorization': 'Basic SjdJRFRra1FmbkQxNGFWVUlPTTB5aDFsOGhRTmszemxVMG01UWRsMjozRmxXZkQ0aHA1N2lvbDhidnhiN3ZhcXNlc1U5d0NScENWM1FhN2FMT1RpUmdHSFFJb0Z0bWprZlhFaThuRWkxdXp6RUc5dHBhR0NhRGVaVUFKODVVSmhKakh1ZVo5NEpoY21IdG1IRGdmbEFsNGJyYkxwQ3JYcDl5ZjZ1c0VSRA=='
                        }
                    });
                    if (!res.ok) {
                        throw new Error('Failed to fetch data');
                    }
                    const data = await res.json();
                    resolve(data);
                } catch (error) {
                    if (operation.retry(error)) {
                        return;
                    }
                    reject(error);
                }
            });
        });
    };

    const fetchCurriculums = async () => {
        await client.connect();
        const db = client.db('course_compass');
        const courses_no_curriculum = await db.collection('courses').find({ curriculums: { $exists: false } }).toArray();
        console.log(courses_no_curriculum.length + ' courses without curriculum');

        const promises = courses_no_curriculum.map(course => {
            return queue.add(async () => {
                try {
                    const uri = `https://www.udemy.com/api-2.0/courses/${course._id}/public-curriculum-items?page_size=100`;
                    const data = await fetchData(uri);
                    while (data.next) {
                        const nextData = await fetchData(data.next);
                        data.results.push(...nextData.results);
                        data.next = nextData.next;
                    }
                    await db.collection('courses').updateOne({ _id: course._id }, { $set: { curriculums: data.results } });
                    console.log('Fetched ' + data.results.length + ' curriculum items for course ' + course._id);
                } catch (error) {
                    console.error('Failed to fetch curriculum for course ' + course._id, error);
                }
            });
        });

        await Promise.all(promises);
        await client.close();
    };

    fetchCurriculums().catch(console.error);
})();
```

---
transition: fade-out
---

# Pengumpulan Data
Udemy API

```json {356-534}
[{
  "_id": 381082,
  "_class": "course",
  "title": "Security Awareness Campaigns (Lite)",
  "url": "/course/security-awareness-campaigns/",
  "is_paid": false,
  "price": "Free",
  "price_detail": null,
  "price_serve_tracking_id": "4LCN4-qXTK6A7bZaDDuWuw",
  "visible_instructors": [
    {
      "_class": "user",
      "title": "Michael Goedeker",
      "name": "Michael",
      "display_name": "Michael Goedeker",
      "job_title": "Cyber Security Researcher, Author, Trainer, M.Sc. CISSP",
      "image_50x50": "https://img-c.udemycdn.com/user/50x50/8980244_c9c3_2.jpg",
      "image_100x100": "https://img-c.udemycdn.com/user/100x100/8980244_c9c3_2.jpg",
      "initials": "MG",
      "url": "/user/michaelgoedeker2/"
    }
  ],
  "image_125_H": "https://img-c.udemycdn.com/course/125_H/381082_8049_6.jpg",
  "image_240x135": "https://img-c.udemycdn.com/course/240x135/381082_8049_6.jpg",
  "is_practice_test_course": false,
  "image_480x270": "https://img-c.udemycdn.com/course/480x270/381082_8049_6.jpg",
  "published_title": "security-awareness-campaigns",
  "tracking_id": "",
  "locale": {
    "_class": "locale",
    "locale": "en_US",
    "title": "English (US)",
    "english_title": "English (US)",
    "simple_english_title": "English"
  },
  "description": "<p>  \t        Security Awareness Campaigns is about the components and reality of what makes awareness campaigns successful and which components are needed in it. This course will cover the basics of a security awareness campaign that is aimed at increasing security levels by addressing social engineering attacks and communicating the basics of awareness and threats companies face today.  </p>  <p>  \t<strong style=\"\">Learn the basic concepts of security awareness campaigns, quickly and easily!</strong>  </p>  <p>  \t    This course goes through relevant research into successful and failed attempts at increasing awareness, also going through complex standards and making them simple and easy to understand.  </p>  <p>  \t    The full version gives you research, tips and information you need to be successful in creating your own security awareness campaign.  </p>  <p>  \t<strong style=\"\">  There are over 22 lectures in the full version that cover:  </strong>  </p>  <ul style=\"\">  \t<li>Introduction to security awareness campaigns</li>  \t<li>What components are needed</li>  \t<li>Security Drivers</li>  \t<li>Vulnerabilities that companies face</li>  \t<li>Business value of campaigns</li>  \t<li>Components of the awareness campaign</li>  \t<li>Security Policy</li>  \t<li>Laptop and Desktop</li>  \t<li>Mobile Devices</li>  \t<li>Data Security and Encryption</li>  \t<li>Incident Response</li>  \t<li>Change Management</li>  \t<li>Security Organization</li>  \t<li>How awareness mitigates risks</li>  \t<li>Practical examples of how awareness has stopped attacks in reality</li>  </ul>  <p>  \t    This course goes through materials and actual projects and gives you the simple scoop on how to create great awareness campaigns that work and which elements you can use in your awareness campaign. It also goes through information that is also important for everyone to know, even if you do not create an awareness campaign, it will help you understand basic concepts.  </p>",
  "headline": "This is the \"lite\" version of Security Awareness Campaigns and is meant to give you an idea of the full course.",
  "num_subscribers": 48269,
  "caption_locales": [
    {
      "_class": "locale",
      "locale": "en_US",
      "title": "English (US)",
      "english_title": "English (US)"
    }
  ],
  "discount": null,
  "discount_price": null,
  "avg_rating": 4.255102,
  "avg_rating_recent": 4.27604,
  "rating": 4.27604,
  "num_reviews": 5733,
  "num_reviews_recent": 51,
  "rating_distribution": [
    {
      "rating": 1,
      "count": 48
    },
    {
      "rating": 2,
      "count": 115
    },
    {
      "rating": 3,
      "count": 992
    },
    {
      "rating": 4,
      "count": 2734
    },
    {
      "rating": 5,
      "count": 1844
    }
  ],
  "favorite_time": null,
  "archive_time": null,
  "earnings": "$0.00",
  "completion_ratio": 0,
  "is_wishlisted": false,
  "num_quizzes": 0,
  "num_lectures": 8,
  "num_published_lectures": 8,
  "num_published_quizzes": 0,
  "num_curriculum_items": 8,
  "num_of_published_curriculum_objects": 8,
  "num_cpe_credits": null,
  "is_private": false,
  "num_practice_tests": 0,
  "num_published_practice_tests": 0,
  "original_price_text": "Free",
  "quality_status": "approved",
  "status_label": "Live",
  "can_edit": false,
  "features": {
    "_class": "course",
    "discussions_create": true,
    "discussions_view": true,
    "discussions_replies_create": true,
    "enroll": true,
    "reviews_create": true,
    "reviews_view": true,
    "reviews_responses_create": true,
    "announcements_comments_view": true,
    "educational_announcements_create": true,
    "promotional_announcements_create": true,
    "promotions_create": true,
    "promotions_view": true,
    "students_view": true
  },
  "gift_url": "https://www.udemy.com/gift/security-awareness-campaigns/",
  "num_invitation_requests": 0,
  "notification_settings": {},
  "is_banned": false,
  "is_published": true,
  "intended_category": null,
  "image_48x27": "https://img-c.udemycdn.com/course/48x27/381082_8049_6.jpg",
  "image_50x50": "https://img-c.udemycdn.com/course/50x50/381082_8049_6.jpg",
  "image_75x75": "https://img-c.udemycdn.com/course/75x75/381082_8049_6.jpg",
  "image_96x54": "https://img-c.udemycdn.com/course/96x54/381082_8049_6.jpg",
  "image_100x100": "https://img-c.udemycdn.com/course/100x100/381082_8049_6.jpg",
  "image_200_H": "https://img-c.udemycdn.com/course/200_H/381082_8049_6.jpg",
  "image_304x171": "https://img-c.udemycdn.com/course/304x171/381082_8049_6.jpg",
  "image_750x422": "https://img-c.udemycdn.com/course/750x422/381082_8049_6.jpg",
  "has_certificate": false,
  "primary_category": {
    "id": 294,
    "title": "IT & Software",
    "title_cleaned": "it-and-software",
    "url": "/courses/it-and-software/",
    "icon_class": "udi udi-it-and-software",
    "type": "category",
    "channel_id": null,
    "_class": "course_category"
  },
  "primary_subcategory": {
    "id": 134,
    "title": "Network & Security",
    "title_cleaned": "network-and-security",
    "url": "/courses/it-and-software/network-and-security/",
    "icon_class": "udi udi-it-and-software",
    "type": "subcategory",
    "channel_id": null,
    "_class": "course_subcategory"
  },
  "is_enrollable_on_mobile": true,
  "is_in_any_ufb_content_collection": false,
  "is_in_user_subscription": false,
  "is_in_subscribed_content_collections": false,
  "has_closed_caption": true,
  "caption_languages": [
    "English [Auto]"
  ],
  "created": "2014-12-30T19:28:49Z",
  "instructional_level": "Beginner Level",
  "instructional_level_simple": "Beginner",
  "estimated_content_length": 33,
  "content_info": "33 total mins",
  "content_info_short": "33 mins",
  "content_length_practice_test_questions": 0,
  "requirements_data": {
    "items": [
      "Just bring your passion for technology and learning how to take security into your own hands"
    ]
  },
  "what_you_will_learn_data": {
    "items": [
      "Lite version of Security Awareness Campaigns training",
      "Basic Security Aspects covered in an awareness campaign"
    ]
  },
  "who_should_attend_data": {
    "items": [
      "Everyone interested in increasing security and privacy of information",
      "Anyone interested in understanding why security awareness is important"
    ]
  },
  "is_available_on_google_app": true,
  "organization_id": null,
  "google_in_app_purchase_price_text": null,
  "promo_asset": {
    "_class": "asset",
    "id": 2455474,
    "asset_type": "Video",
    "title": "Security Awareness Campaigns_Intro.mp4",
    "title_cleaned": "securityawarenesscampaignsintromp4",
    "description": "",
    "length": 89,
    "status": 1,
    "download_urls": {
      "Video": [
        {
          "type": "video/mp4",
          "label": "720",
          "file": "https://mp4-c.udemycdn.com/2015-01-07_02-32-47-7fb6a22157d772d23d20e899771babfb/WebHD_720p.mp4?Expires=1720192474&Signature=8CLQFhD-SXvH~MPW8WbB7-27xUyHOk4h2YyP-zni1lQUwXZb9~DI3xvv-Jrh8VIpYFm1WeMtitDtlB6ICg8zAsQVH6Dgn8j1pQH7ahZBuZTNB3yND4vpEoTJbknp55JQyzxhMXn~9Z90OGDa1zFDEGB4NuSRjqSqIQPvMy6eQMNkKnWFgY9PadiqJL-7kYZR4BoH913fFSBw7cSFPcXPrLOofK4QE8VWBWEt9BzaQgsAu6TOBc3NJfh~OdymxXno5a3FvcdJIu5Cz8aw-F~XXFTmaW89sXtBh0w5cm24pEWZmAOruYN0vQW3-~QL8Daz1AoFCz-lGF6iLdljdw068A__&Key-Pair-Id=K3MG148K9RIRF4"
        },
        {
          "type": "video/mp4",
          "label": "360",
          "file": "https://mp4-c.udemycdn.com/2015-01-07_02-32-47-7fb6a22157d772d23d20e899771babfb/WebHD.mp4?Expires=1720192474&Signature=gw31xCW2k4R~3YS7BgPYUVb1MlLRrm4p20cBAG4YsgEYiH21W~uVmYYXD4M3uKeAuoAOg87UxQDWQyyU05GvfDE-t3XvnXlMOSbKpo3Mpwv9tmCK~mrP~PawUWyO09uya3m4rkmtloVy7aZpK5soWQTIWyGwr0fYV0ivS4LmCdP6musLHzg1d1j4cSX9HtcJ3iWyRfPBJ-mZgiyQpZONGlzzBCcx9apHgNCjKGCYXkvjgVU1LaPrd~IZh9mUSLNE~3HZtEloj-X4UB035r2bdUaCb~BAI~aE6qsUAmclLEj50Xm4BwA58q7x49vZ3E8LBwkV0ysVwIJoq9Q5lMkaOg__&Key-Pair-Id=K3MG148K9RIRF4"
        }
      ]
    }
  },
  "is_user_subscribed": false,
  "apple_in_app_product_id": null,
  "is_available_on_ios": true,
  "google_in_app_product_id": null,
  "faq": [
    {
      "question": "How long do I have access to the course materials?",
      "answer": "You can view and review the lecture materials indefinitely, like an on-demand channel."
    },
    {
      "question": "Can I take my courses with me wherever I go?",
      "answer": "Definitely! If you have an internet connection, courses on Udemy are available on any device at any time. If you don't have an internet connection, some instructors also let their students download course lectures. That's up to the instructor though, so make sure you get on their good side!"
    }
  ],
  "apple_in_app_purchase_price_text": null,
  "type_label": "course",
  "google_in_app_price_detail": null,
  "apple_in_app_price_detail": null,
  "quality_review_process": {
    "_class": "quality_review_process",
    "id": 3030,
    "status": "approved",
    "score": 50,
    "admin_rating": 7
  },
  "is_organization_only": false,
  "is_cpe_compliant": false,
  "cpe_field_of_study": null,
  "cpe_program_level": null,
  "was_ever_published": true,
  "buyable_object_type": "course",
  "published_time": "2015-01-05T00:53:30Z",
  "is_marketing_boost_agreed": true,
  "is_owned_by_instructor_team": false,
  "is_owner_terms_banned": false,
  "is_taking_disabled": false,
  "content_length_video": 1589,
  "checkout_url": "/payment/checkout/express/course/381082/",
  "prerequisites": [
    "Just bring your passion for technology and learning how to take security into your own hands"
  ],
  "objectives": [
    "Lite version of Security Awareness Campaigns training",
    "Basic Security Aspects covered in an awareness campaign"
  ],
  "objectives_summary": [
    "Lite version of Security Awareness Campaigns training",
    "Basic Security Aspects covered in an awareness campaign"
  ],
  "target_audiences": [
    "Everyone interested in increasing security and privacy of information",
    "Anyone interested in understanding why security awareness is important"
  ],
  "last_accessed_time": null,
  "enrollment_time": null,
  "course_has_labels": [
    {
      "_class": "course_has_label",
      "id": 90654,
      "label": {
        "_class": "course_label",
        "id": 5316,
        "title": "Cyber Security",
        "url": "/topic/cyber-security/",
        "icon_class": "udi udi-line-star",
        "type": "topic",
        "display_name": "Cyber Security"
      },
      "is_primary": true
    }
  ],
  "bestseller_badge_content": null,
  "badges": [],
  "free_course_subscribe_url": "/course/subscribe/?courseId=381082",
  "is_recently_published": false,
  "last_update_date": "2015-01-07",
  "num_article_assets": 0,
  "num_coding_exercises": 0,
  "num_assignments": 0,
  "num_additional_assets": 0,
  "preview_url": "/course/381082/preview/",
  "landing_preview_as_guest_url": "/course/security-awareness-campaigns/?instructorPreviewMode=guest",
  "context_info": {
    "category": {
      "id": 294,
      "title": "IT & Software",
      "url": "/courses/it-and-software/",
      "tracking_object_type": "cat"
    },
    "subcategory": null,
    "label": {
      "id": 5316,
      "display_name": "Cyber Security",
      "title": "Cyber Security",
      "topic_channel_url": "/topic/cyber-security/",
      "url": "/topic/cyber-security/",
      "tracking_object_type": "cl"
    }
  },
  "has_sufficient_preview_length": true,
  "has_org_only_setting": false,
  "has_labs_in_course_prompt_setting": false,
  "is_draft": false,
  "custom_category_ids": [],
  "alternate_redirect_course_id": 0,
  "is_approved": true,
  "is_organization_eligible": true,
  "instructor_status": {
    "_class": "instructor_course_status",
    "id": 185116,
    "user": {
      "_class": "user",
      "title": "Michael Goedeker",
      "name": "Michael",
      "display_name": "Michael Goedeker"
    },
    "status": 1,
    "respond_time_frame": "1 week",
    "available_date": null
  },
  "available_features": [],
  "enroll_url": "/course/381082/enroll/",
  "learn_url": "/course/security-awareness-campaigns/learn/",
  "retirement_date": null,
  "is_course_available_in_org": null,
  "is_in_personal_plan_collection": false,
  "is_in_premium": false,
  "is_language_course": false,
  "has_508_closed_captions": false,
  "is_coding_exercises_badge_eligible": false,
  "content_collections": [],
  "is_course_in_ub_ever": false,
  "has_course_a_published_coding_exercise": false,
  "published_lecture_ids": [
    2179026,
    2170568,
    2170570,
    2176496,
    2178700,
    2178882,
    2178586,
    2170556
  ],
  "predictive_score": null,
  "relevancy_score": null,
  "input_features": null,
  "lecture_search_result": null,
  "curriculum_lectures": [],
  "order_in_results": null,
  "curriculum_items": [],
  "instructor_name": null,
  "curriculums": [
    {
      "_class": "lecture",
      "id": 2179026,
      "title": "Introduction into this course.",
      "created": "2015-01-05T00:40:33Z",
      "description": "",
      "title_cleaned": "introduction-into-this-course",
      "is_published": true,
      "transcript": null,
      "is_downloadable": true,
      "is_free": false,
      "asset": {
        "_class": "asset",
        "id": 2443750,
        "asset_type": "Audio",
        "title": "Intro ",
        "created": "2015-01-05T14:57:15Z"
      },
      "sort_order": 8,
      "can_be_previewed": false
    },
    {
      "_class": "chapter",
      "id": 574070,
      "created": "2015-01-03T12:59:13Z",
      "sort_order": 7,
      "title": "Security Awareness Campaigns (Lite)",
      "description": "Understand Security Drivers, Vulnerable areas of a business or entity and some insight on research into security awareness campaigns.",
      "is_published": true
    },
    {
      "_class": "lecture",
      "id": 2170568,
      "title": "Research into Security Awareness and Cyber threats",
      "created": "2015-01-03T13:00:07Z",
      "description": "",
      "title_cleaned": "research-into-security-awareness-and-cyber-threats",
      "is_published": true,
      "transcript": null,
      "is_downloadable": false,
      "is_free": true,
      "asset": {
        "_class": "asset",
        "id": 2440668,
        "asset_type": "Video",
        "title": "Introduction.mov",
        "created": "2015-01-05T00:09:41Z"
      },
      "sort_order": 6,
      "can_be_previewed": false
    },
    {
      "_class": "lecture",
      "id": 2170570,
      "title": "Security Awareness and Training (Status Quo)",
      "created": "2015-01-03T13:00:30Z",
      "description": "",
      "title_cleaned": "security-awareness-and-training-status-quo",
      "is_published": true,
      "transcript": null,
      "is_downloadable": false,
      "is_free": false,
      "asset": {
        "_class": "asset",
        "id": 2440216,
        "asset_type": "Video",
        "title": "toTeach_or_Not.mov",
        "created": "2015-01-04T22:35:43Z"
      },
      "sort_order": 5,
      "can_be_previewed": false
    },
    {
      "_class": "lecture",
      "id": 2176496,
      "title": "Security Drivers of Awareness",
      "created": "2015-01-04T16:37:55Z",
      "description": "<p> \tShort discussion on security drivers of a security awareness campaign. Please keep in mind that the full course has much more detail. </p>",
      "title_cleaned": "security-drivers-of-awareness",
      "is_published": true,
      "transcript": null,
      "is_downloadable": false,
      "is_free": false,
      "asset": {
        "_class": "asset",
        "id": 2440280,
        "asset_type": "Video",
        "title": "security_drvrs.mov",
        "created": "2015-01-04T22:45:10Z"
      },
      "sort_order": 4,
      "can_be_previewed": false
    },
    {
      "_class": "lecture",
      "id": 2178700,
      "title": "Areas of vulnerability",
      "created": "2015-01-04T23:25:22Z",
      "description": "",
      "title_cleaned": "areas-of-vulnerability",
      "is_published": true,
      "transcript": null,
      "is_downloadable": false,
      "is_free": false,
      "asset": {
        "_class": "asset",
        "id": 2440724,
        "asset_type": "Video",
        "title": "Vulnerability factors in business.mov",
        "created": "2015-01-05T00:26:53Z"
      },
      "sort_order": 3,
      "can_be_previewed": false
    },
    {
      "_class": "lecture",
      "id": 2178882,
      "title": "Some objectives of a security awareness campaign",
      "created": "2015-01-05T00:06:57Z",
      "description": "<p> \tThis lecture discusses some of the objectives of a security awareness campaign. </p>",
      "title_cleaned": "some-objectives-of-a-security-awareness-campaign",
      "is_published": true,
      "transcript": null,
      "is_downloadable": false,
      "is_free": false,
      "asset": {
        "_class": "asset",
        "id": 2455728,
        "asset_type": "Video",
        "title": "Voila_Capture 2015-01-07_12-52-19_PM.mov",
        "created": "2015-01-07T11:55:45Z"
      },
      "sort_order": 2,
      "can_be_previewed": false
    },
    {
      "_class": "lecture",
      "id": 2178586,
      "title": "Summary of the lite version",
      "created": "2015-01-04T22:43:50Z",
      "description": "<p> \tShort summary of the lite course and some more detail about the full course. </p>",
      "title_cleaned": "summary-of-the-lite-version",
      "is_published": true,
      "transcript": null,
      "is_downloadable": true,
      "is_free": false,
      "asset": {
        "_class": "asset",
        "id": 2440730,
        "asset_type": "Audio",
        "title": "Summary ",
        "created": "2015-01-05T00:29:14Z"
      },
      "sort_order": 1,
      "can_be_previewed": false
    },
    {
      "_class": "lecture",
      "id": 2170556,
      "title": "Additional info on methodologies and standards",
      "created": "2015-01-03T12:59:13Z",
      "description": "<p> \t Some additional information on ISACA, ISC2 and other methodologies that can be used to guide the creation of your security awareness campaign. </p>",
      "title_cleaned": "additional-info-on-methodologies-and-standards",
      "is_published": true,
      "transcript": null,
      "is_downloadable": true,
      "is_free": false,
      "asset": {
        "_class": "asset",
        "id": 2442406,
        "asset_type": "Audio",
        "title": "Introduction",
        "created": "2015-01-05T07:48:01Z"
      },
      "sort_order": 0,
      "can_be_previewed": false
    }
  ]
}]
```

---
transition: fade-out
---

# Pengumpulan Data
Penyimpanan ke Database

<img src="./database1.png" alt="Penyimpanan ke Database" class="h-100">

---
transition: fade-out
---

# Pengumpulan Data
Penyimpanan ke Database

<img src="./database2.png" alt="Penyimpanan ke Database" class="h-100">

---
transition: fade-out
---

# Pemrosesan Data
```mermaid
---
config:
  layout: fixed
---
flowchart TD
    %% Source Data
    subgraph S1 [Source Data]
      direction TB
      A["Subtopics<br>title, description"]
      C["Courses<br>title, description, headline"]
      E["Chapters<br>title, description"]
      G["Curriculum Items<br>title, description"]
    end

    %% Processing with nested subgraphs
    subgraph S2 [Processing]
      direction TB
      
      subgraph S2A [" "]
        direction TB
        B["Processing Subtopics"]
        D["Processing Courses"]
        F["Processing Chapters"]
        H["Processing Curriculum Items"]
      end
      
      subgraph S2B [" "]
        direction TB
        I["Embedding Vector<br>untuk Similarity Search"]
        J["TSQuery<br>untuk Full Text Search"]
        K["Embedding Vector<br>untuk Similarity Search"]
        L["TSVector<br>untuk Full Text Search"]
        M["Embedding Vector<br>untuk Similarity Search"]
        N["TSVector<br>untuk Full Text Search"]
        O["Embedding Vector<br>untuk Similarity Search"]
        P["TSVector<br>untuk Full Text Search"]
      end
    end

   %% Search Stage
   subgraph S3 [Search]
     direction TB
     Q{"For Each Subtopic"}
     R["Similarity Search"]
     S["Full Text Search"]
   end

    %% Ranking & Results
    subgraph S4 [Ranking & Results]
      direction TB
      T["Top 100 Courses<br>by Similarity"]
      U["Top 1000 Chapters<br>by Similarity"]
      V["Top 5000 Curriculum Items<br>by Similarity"]
      W["Top 100 Courses<br>by Score"]
      X["Top 1000 Chapters<br>by Score"]
      Y["Top 5000 Curriculum Items<br>by Score"]
    end

    %% Storage
    subgraph S5 [Storage]
      direction TB
      Z1["top_courses_by_similarity"]
      Z2["top_chapters_by_similarity"]
      Z3["top_curriculum_items_by_similarity"]
      Z4["top_courses_by_score"]
      Z5["top_chapters_by_score"]
      Z6["top_curriculum_items_by_score"]
    end

    %% Connections
    A --> B
    C --> D
    E --> F
    G --> H
    B --> I & J
    D --> K & L
    F --> M & N
    H --> O & P
    I --> Q
    J --> Q
    Q --> R & S
    R --> T & U & V
    S --> W & X & Y
    T --> Z1
    U --> Z2
    V --> Z3
    W --> Z4
    X --> Z5
    Y --> Z6

    %% Dotted lines for additional usage
    K -.-> R
    L -.-> S
    M -.-> R
    N -.-> S
    O -.-> R
    P -.-> S

    %% Class coloring
    class A,C,E,G sourceData
    class B,D,F,H dataProcessing
    class I,J,K,L,M,N,O,P vectorGeneration
    class Q,R,S search
    class T,U,V,W,X,Y results
    class Z1,Z2,Z3,Z4,Z5,Z6 storage
    classDef sourceData fill:#e1f5fe
    classDef dataProcessing fill:#f3e5f5
    classDef vectorGeneration fill:#e8f5e8
    classDef search fill:#fff3e0
    classDef results fill:#ffecb3
    classDef storage fill:#fce4ec
```

---
layout: default
---

# Gambaran Umum Pipeline Pemrosesan Data

Pemrosesan data dalam penelitian ini dirancang dengan arsitektur *pipeline* yang terdiri dari lima tahap utama:
* **Source Data** (data sumber)
* **Processing** (pemrosesan)
* **Search** (pencarian)
* **Ranking & Results** (pemeringkatan hasil)
* **Storage** (penyimpanan)

---
transition: fade-out
---

# Tahap 1: Input Data (Source Data)

Data input yang diproses terdiri dari empat jenis entitas utama:
* **Subtopics:** Berisi informasi judul dan konten dari subtopik pembelajaran.
* **Courses:** Berisi informasi judul, deskripsi, dan *headline* dari kursus.
* **Chapters:** Berisi informasi judul dan deskripsi dari *chapter* dalam kursus.
* **Curriculum items:** Berisi informasi judul dan deskripsi dari item kurikulum.

---
transition: fade-out
---

# Tahap 2: Pemrosesan Data - Persiapan Semantic Search

### Pemrosesan *Embedding Vector*
* Untuk *semantic search*, sistem menggunakan model `alibaba-nlp/gte-multilingual-base` untuk mengonversi teks menjadi *embedding vector*.
* Model ini dipilih karena kemampuannya dalam menangani teks multibahasa dan menghasilkan representasi semantik berkualitas tinggi.

---
transition: fade-out
---

# Tahap 2: Pemrosesan Data - Persiapan Semantic Search

```python {1-6|8-14|16|17-24|29-39|43-59|65-66}
import psycopg2
import argparse
from sentence_transformers import SentenceTransformer
import time

batch_size = 1

parser = argparse.ArgumentParser()
parser.add_argument("--table", type=str, default="course")
parser.add_argument("--order", type=str, default="ASC")

args = parser.parse_args()
table = args.table
order = args.order

model = SentenceTransformer("Alibaba-NLP/gte-multilingual-base", trust_remote_code=True)
connection = psycopg2.connect(
    dbname='course_compass',
    user='postgres',
    password='fck39su41',
    host='localhost',
    port='5432'
)
cursor = connection.cursor()

print(f"Start processing {table} embeddings")


if table == "course":
    columns = "CONCAT(ci.title, ' ', ci.description, ' ', ci.headline)"
else:
    columns = "CONCAT(ci.title, ' ', ci.description)"

sql = f"SELECT ci.id, {columns} FROM {table}s ci LEFT JOIN {table}_embeddings cie ON ci.id = cie.id WHERE cie.id IS NULL ORDER BY ci.id {order}"
cursor.execute(sql)
curriculum_items = cursor.fetchall()

ids = [item[0] for item in curriculum_items]
texts = [item[1] for item in curriculum_items]

start = time.time()

for start_idx in range(0, len(texts), batch_size):
    batch_texts = texts[start_idx:start_idx + batch_size]
    batch_ids = ids[start_idx:start_idx + batch_size]

    es = time.time()
    embeddings = model.encode(batch_texts, normalize_embeddings=False)
    embeddings = [embedding.tolist() for embedding in embeddings]
    ee = time.time()

    qs = time.time()
    sql = f"INSERT INTO {table}_embeddings (id, embedding) VALUES %s"
    values = ", ".join(["(%s, %s)"] * len(batch_ids))
    sql = sql % values
    values = [val for pair in zip(batch_ids, embeddings) for val in pair]
    cursor.execute(sql, values)

    connection.commit()
    qe = time.time()

    current = time.time()
    print(f"Processed {start_idx + len(batch_texts)}/{len(texts)} items ({(start_idx + len(batch_texts)) / len(texts) * 100}%) elapsed: {current - start} embeddings: {ee - es} query: {qe - qs}")

cursor.close()
connection.close()

print(f"Done")
```

---
transition: fade-out
---

# Tahap 2: Pemrosesan Data - Persiapan Semantic Search

* Title: Essentials in JavaScript ES6 - A Fun and Clear Introduction
* Description: Turn yourself into a **highly-demanded** software engineer and developer by following this tutorial on **JavaScript ES6**. As one the most highly-paid languages, learning ES6 will open so many jobs and opportunities for you.
* Headline: A creative and fun course on JavaScript ES6! Has Webpack, Babel, React, and all the new syntax you need to code in ES6!

```json
[-0.031157354,0.037014585,-0.065081045,-0.03348914,0.10405791,0.044005916,-0.014843085,-0.024229443,-0.02295062,-0.009051306,-0.09202981,-0.05233119,-0.09668033,0.0650653,0.0031455867,0.08355515,0.082801856,0.009331086,0.044355795,-0.041608114,0.025650725,0.03423557,0.015049549,-0.010978745,0.012606279,0.08410892,0.057274736,-0.11738658,0.020514412,0.010604737,-0.08032848,-0.007621971,0.041266676,0.04236728,0.10508883,-0.030370455,-0.033793073,-0.04099591,0.0081177745,0.01622111,0.01456761,0.01888089,-0.0068069524,0.032508887,0.015766906,0.026280388,-0.018658187,0.0588392,0.0055771065,0.07235082,-0.078373745,-0.0012995914,0.026432509,-0.0052533248,0.048280556,0.0378242,-0.06967963,0.004436541,0.034977,-0.029137082,0.08652611,-0.0026216407,0.005432833,-0.066432536,-0.019747833,0.02915253,-0.008880698,-0.002037517,0.07742111,-0.0012884645,-0.013202116,-0.013090367,-0.03129617,0.0219501,-0.0065787598,0.06248106,-0.09455283,-0.03923178,0.0064142914,-0.009234958,-0.0113229165,0.0011974401,0.009520172,0.053823903,0.0033723337,-0.0025826646,-0.024723046,-0.02749678,-0.05643912,0.02230134,-0.0058208904,0.09560566,0.020949038,-0.03496615,0.008146807,0.0678014,-0.0285125,0.03336407,-0.00056665955,0.06725317,0.0034020897,-0.06764333,-0.01848094,-0.0035893968,0.029845497,0.013935731,0.024873152,0.007250167,-0.020195028,-0.014460693,-0.044757914,-0.06683966,-0.07701728,0.008360767,-0.03809353,0.02083081,0.037519414,-0.011162146,0.03083236,0.039805997,-0.011272383,0.037759375,-0.052723326,-0.023321852,-0.04243077,0.004667242,-0.05341204,0.030265994,-0.059389405,-0.054183386,0.023272656,0.01608579,-0.007872133,-0.036290396,0.015573913,0.016916716,-0.008997819,0.09253078,-0.020321896,-0.016621485,-0.034220744,0.044385955,-0.085975476,-0.0137158455,-0.028505627,-0.019365394,-0.045682374,0.00084101956,-0.0034055351,0.04007262,0.040018138,0.03217426,0.016299684,-0.029133655,0.037281897,-0.06067717,-0.009992141,0.024278617,-0.022986824,-0.027287288,0.051554948,0.012920469,0.019302035,-0.004684848,-0.05837361,0.013184414,0.011793052,-0.017033724,-0.011248224,0.041258875,-0.063836925,0.019899866,0.0260494,-0.020970516,-0.03832714,-0.039549537,-0.02875715,0.010387615,-0.07130389,0.047730364,0.044396073,-0.01200978,0.0049157124,0.053495497,0.07377822,-0.010645767,-0.06504512,0.009883248,-0.09685484,-0.03749386,-0.043109726,0.002415957,-0.046515204,0.018314648,-3.6515386e-05,0.001014518,-0.04433284,0.0024178943,0.03474638,0.015859352,-0.026334204,0.012908972,-0.03161215,0.032196485,-0.018507248,-0.00069923466,-0.045372985,-0.017244086,-0.016789103,-0.099690266,0.040559627,0.036376256,-0.029505732,0.039537303,0.020391004,-0.0016065339,0.021804594,-0.008909148,0.0641395,-0.04628176,-0.02232339,-0.015227417,-0.023208428,-0.052734267,-0.048410736,0.01679966,-0.03395153,0.022003353,0.008656724,-0.034790553,0.039660677,0.014696459,0.00029520554,-0.016988663,0.0033446858,-0.017908484,-0.020270206,0.012542414,-0.015342076,0.020327207,-0.014168402,-0.0025503582,0.027820934,0.012504931,0.06856342,3.2796437e-05,-0.010349446,-0.01369873,-0.03388474,0.009967707,-0.027128402,0.0025141786,-0.08196666,0.034710873,-0.007462597,-0.016965711,-0.002062515,0.01963977,-0.036324706,-0.062449947,0.014217305,-0.02479798,-0.014135909,0.032625377,0.048221547,-0.06844998,0.046330173,0.052829135,-0.070540965,-0.0077100126,0.01578321,0.0063579343,0.020831166,-0.011695088,0.006644,0.041528877,-0.032758657,-0.040963218,-0.009697597,0.008456013,0.026363779,0.024483133,0.03901067,0.020234978,-0.025172895,0.068133704,0.018880734,0.013007969,0.0064880084,0.011572106,-0.022252517,-0.01568815,-0.029582439,0.07088734,0.03791962,0.020102603,0.031280827,-0.011588113,-0.001116649,-0.045493834,0.018282514,0.0017142501,0.024357265,0.01246752,-0.026983028,-0.036658734,-0.09883895,-0.013804793,-0.014996422,-0.017673584,0.006374972,0.012702968,0.007880859,-0.010432218,0.027374836,0.01949126,0.017399715,0.05651211,-0.023582688,-0.019566149,0.05728204,0.054413825,-0.06635464,0.04281496,-0.010903766,-0.016023258,0.056509253,0.017882358,-0.042622257,-0.015672952,-0.014650501,0.01592777,0.03385369,-0.060338877,0.035497643,0.0770307,0.023191722,-0.02132056,0.02281797,0.008590697,0.04889164,0.04638229,-0.07936737,0.009282777,0.05266443,-0.020498132,0.06162803,-0.0027190363,0.013992753,-0.0017713142,-0.014764364,0.01257386,0.07686594,0.066805735,0.006137303,0.033425204,-0.0037298994,0.055504538,-0.009705929,0.008634117,0.021089248,0.0066922605,-0.0056643197,0.024336426,-0.00061500986,-0.016167406,-0.045004267,-0.026054665,-0.05666941,-0.035886608,0.040719558,-0.0073652784,0.038470257,0.055979315,-0.025352694,0.027842019,0.01582488,0.062156867,-0.021864139,0.0032183349,-0.0042712805,-1.8188115e-05,-0.030239044,0.0051618735,0.01794301,-0.06266282,-0.038796928,0.0029044582,-0.015476587,0.026177185,0.030885877,-0.052054405,0.020494724,0.024035065,0.032172382,-0.009263959,0.026950605,0.007454596,-0.033313114,0.054140396,0.0101184165,0.059799507,0.023975054,0.033568684,0.030313618,0.05330558,0.020474061,-0.03489067,0.0253921,0.009496921,0.034635402,0.03225108,-0.0013778899,-0.041188326,-0.021735629,-0.007947902,0.027130615,0.043449815,0.13784638,0.015547535,0.012451713,0.051257867,0.04166961,-0.04157504,-0.011917666,-0.020862844,0.016828675,0.066146396,-0.036083102,0.025907882,-0.039725825,-0.03661371,-0.011892968,-0.0046980744,-0.021590244,-0.0261668,-0.04061158,0.06216446,0.015131626,-0.07597285,-0.0066659367,0.013867709,0.026713535,0.008414819,0.0040816935,0.04250434,0.019340325,0.054503158,0.0150571335,0.02745722,-0.06738341,0.015551136,-0.029871,-0.012020437,0.07051158,0.0017597912,-0.023729328,0.0064500663,-0.06218909,0.014245668,0.0008539739,-0.030085698,-0.006574788,0.032855902,0.039756402,0.042737767,-0.0021247505,0.0037357737,0.03412713,0.03651447,-0.0749578,0.007294897,0.0025616325,-0.024240686,0.013332986,0.040741306,-0.059936713,0.06000219,0.03983926,-0.056641992,0.0007151659,0.00417746,0.00084494345,0.020836072,-0.006578544,0.05061423,-0.0015337525,-0.06842832,-0.026325865,0.012242063,0.05216707,0.018645134,-0.04059319,-0.01959625,-0.0053151683,0.011186382,0.019347047,-0.038728643,-0.030169537,0.041909978,-0.017367851,-0.02742925,-0.010539125,-0.010087684,0.04117643,-0.049540706,0.0061991573,-0.0067655896,-0.023360828,-0.0015286618,-0.014325355,-0.025298277,-0.01819121,-0.0038652462,-0.03346911,0.045718435,-0.04622732,0.017526038,-0.03709412,0.016277088,0.042017218,-0.009106135,-0.0025738042,0.02304279,0.102304555,-0.040320884,-0.021153962,0.0034619905,-0.026394444,0.0020055708,0.02740654,0.09121462,0.0011657887,0.042814672,0.025382983,0.026337313,0.0013792041,0.0815464,0.016532585,-0.054291856,-0.014110539,-0.028380046,-0.027752085,0.00067365926,0.036873482,0.009200666,0.031794716,-0.01544892,-0.029074641,-0.053958256,-0.014045273,0.015944373,0.04034432,0.015137224,0.004263612,0.020092763,-0.00012292158,-0.04860119,-0.017379833,0.0038061796,-0.021172341,-0.006079156,0.037486035,0.062664054,0.042816028,-0.0005631289,0.047288064,0.011302347,-0.014058567,-0.020339191,0.019020142,0.025041485,0.092695415,-0.03995759,-0.00078941335,0.002297208,-0.029875502,0.017447226,0.020648226,-0.01938111,-0.099400006,-0.054826774,-0.025149237,0.016101863,0.004251528,0.014899533,0.005716938,0.0057370993,0.014486912,-0.0028687832,-0.020932322,0.021703469,-0.0074790856,-0.0133636575,0.059312336,0.03743813,0.025788615,-0.016970659,0.035619937,0.018515961,0.00165657,-0.028586337,0.061847884,0.0650044,-0.01352496,0.03214105,0.0075616506,-0.02548094,-0.006575634,0.06242499,0.049833443,-0.0060064555,0.017376723,0.012791345,-0.001967127,0.005959045,0.0008990972,0.0110575985,-0.030556662,0.02530576,-0.030263163,0.023316579,0.023827126,0.024380663,-0.009486122,0.043623697,0.0016874783,-0.06960794,-0.06023241,-0.024476187,-0.041943505,0.06383155,0.021380043,-0.01231616,-0.013669631,-0.016483646,-0.033946864,0.039954364,-0.011620083,-0.03277153,-0.035388306,0.017022494,0.017867986,0.010693397,0.022266071,0.043310873,0.007249002,-0.039269324,-0.03428133,0.036239553,0.017234588,-0.049576607,-0.032914225,0.032011393,0.004876566,0.003944029,-0.027811535,0.0317404,0.081364,0.03532675,-0.01125285,0.002701097,0.026916636,-0.064668536,-0.054593705,-0.03934221,0.0009164786,0.038360022,-0.0038935721,0.011319596,-0.032027014,-0.017818488,-0.03599777,0.008451635,-0.030059049,-0.058952525,-0.019885505,-0.034402676,-0.03934424,0.03128727,-0.0004893861,-0.022502545,-0.025148222,0.014132091,-0.023115799,0.00925448,0.01366174,0.019403191,0.033690564,0.032240424,0.066389866,0.007612549,0.013412003,0.017656442,0.009839567,-0.003583926,-0.023207335,-0.006799556,-0.0036135619,-0.00799028,0.011191348,0.00636117,-0.02353469,-0.033488877,-0.03902685,-0.0030161273,0.031620238,-0.024324851,0.010170068,-0.020698769,0.03991061,-0.027342912,-0.057430167,0.021512255,-0.024906151,-0.046477012,0.0013456804,0.030956361,-0.019535594,0.017570917,-0.052281316,-0.010797393,-0.024783561,0.03463125,-0.026913542,0.00013881088,0.034258723,-0.018122852,-0.009192663,-0.0025273701,-0.006630759,0.030227287,0.02650102,0.014259623,0.026270028,-0.060668275,-0.033322893,-0.028716732,0.014711409,-0.045175757,-0.004429968,-0.022470174,0.0029293606,0.0059564714,-0.010146351,0.060810138,0.032364424,0.015525437,-0.027548742,0.049058944,0.052177913,0.029542912,-0.009399288,0.050103344,-0.025566503,-0.034571253,0.009398232,-0.079295255,-0.0036807496,0.0033334622,-0.07593464,-0.017268533,-0.00067147106,-0.030305106,-0.029338313,-0.029832,-0.0077486318,-0.01589878]
```

---
transition: fade-out
---

# Tahap 2: Pemrosesan Data - Persiapan Keyword Search

### Pemrosesan TSQuery dan TSVector
* Untuk *keyword search*, sistem menggunakan fitur *Full-Text Search* PostgreSQL yang terdiri dari dua komponen utama:
    * **TSVector (Text Search Vector):** Representasi teks yang telah diproses dan dioptimalkan untuk pencarian, mengubah teks biasa menjadi daftar kata-kata unik beserta posisinya dalam dokumen, dengan menghilangkan kata-kata tidak penting.
    * **TSQuery (Text Search Query):** Representasi dari *query* pencarian yang telah diproses, mengubah kata kunci pencarian menjadi format yang dapat dicocokkan dengan TSVector menggunakan operator logika.
* Sistem mengimplementasikan algoritma khusus untuk membentuk TSQuery dari subtopik dan TSVector dari entitas lainnya.

---
transition: fade-out
---

# Tahap 2: Pemrosesan Data - Persiapan Keyword Search

```python {6-14|16|18-47|49-58}
import psycopg2
import nltk
from collections import Counter
from itertools import combinations

connection = psycopg2.connect(
    dbname='course_compass',
    user='postgres',
    password='fck39su41',
    host='localhost',
    port='5432'
)

cursor = connection.cursor()

stop_words = set(nltk.corpus.stopwords.words('english'))

def generate_tsquery(content, title):
    words = nltk.tokenize.word_tokenize(content)

    pos_tags = nltk.pos_tag(words)

    keywords = [word.lower() for word, tag in pos_tags if word.isalnum() and word.lower() not in stop_words and (tag.startswith('NN'))]

    prefix = ""

    if title.lower() in keywords:
        prefix += f"{title.lower()} & "
    while title.lower() in keywords:
        keywords.remove(title.lower())
    
    word_counts = Counter(keywords)

    sorted_words = [word for word, _ in word_counts.most_common()]  # Hanya ambil kata-kata, bukan hitungan

    main_words = sorted_words[:4]
    additional_words = sorted_words[4:]

    main_combinations = " | ".join(
        f"({a} & {b})" for a, b in combinations(main_words, 2)
    )

    additional_part = " | ".join(additional_words)

    final_result = f"{prefix}({main_combinations}) & ({additional_part})"

    return final_result

sql = "SELECT id, title, content FROM subtopics"
cursor.execute(sql)
topics = cursor.fetchall()

for id, title, content in topics:
    content = content.replace('<p>', '').replace('</p>', '')
    tsquery = generate_tsquery(content, title)
    cursor.execute("UPDATE subtopics SET tsquery = %s WHERE id = %s", (tsquery, id))

connection.commit()
```

---
transition: fade-out
---

# Tahap 2: Pemrosesan Data - Pembentukan TSQuery

### Tahapan Pembentukan TSQuery:
* Analisis linguistik menggunakan NLTK untuk tokenisasi dan *POS tagging*.
* Ekstraksi kata benda sebagai kata kunci utama.
* Mengurutkan kata berdasarkan frekuensi kemunculan dalam teks.
* Pembagian kata menjadi `main_words` (4 teratas) dan `additional_words`.
* Pembentukan *query* dengan kombinasi operator `&` dan `|`.

**Contoh Hasil TSQuery:**
* Judul: “Browsers and how they work?”
* Konten: “A web browser is a software application that enables a user to access and display web pages or other online content through its graphical user interface.”
* Hasil TSQuery: “((web & user) | (web & browser) | (web & software) | (user & browser) | (user & software) | (browser & software)) & (application | access | display | pages | content | interface)”.

---
transition: fade-out
---
# Tahap 2: Pemrosesan Data - Pembentukan TSVector

```sql
SELECT
    id,
    title,
    description,
    headline,
    to_tsvector('english', title || ' ' || description || ' ' || headline) AS combined_tsvector
FROM
    courses;
```

* Title: Essentials in JavaScript ES6 - A Fun and Clear Introduction
* Description: Turn yourself into a **highly-demanded** software engineer and developer by following this tutorial on **JavaScript ES6**. As one the most highly-paid languages, learning ES6 will open so many jobs and opportunities for you.
* Headline: A creative and fun course on JavaScript ES6! Has Webpack, Babel, React, and all the new syntax you need to code in ES6!

```
'also':99 'appear':115 'approach':107 'babel':198 'behind':85 'break':101,123 'challeng':95 'clear':8 'code':73,94,100,187,208 'concept':98 'content':54 'cours':48,109,144,172,192 'creativ':189 'demand':16 'develop':20 'dive':181 'divers':53 'either':169 'engin':18 'es6':4,27,37,59,150,184,195,210 'especi':120 'essenti':1 'even':129 'experi':158 'explain':82 'featur':49 'film':67 'find':162 'follow':22 'fun':6,65,191 'get':70 'give':145 'great':147 'high':15,33 'highly-demand':14 'highly-paid':32 'humor':136 'inform':63 'intro':148 'introduct':9 'javascript':3,26,135,183,194 'job':42 'joke':114 'key':97 'keyword':90 'knee':132 'know':126 'languag':35,168 'learn':36,58 'let':105,177 'line':88 'll':57,161 'lot':156 'make':79 'mani':41 'might':128 'need':206 'new':87,141,203 'nice':164 'one':29 'open':39 'opportun':44 'option':91 'overview':165 'pace':113 'paid':34 'perfect':174 'quizz':92 're':139 'react':199 'reason':84 'reinforc':96 'section':104 'slap':130 'softwar':17 'start':186 'still':140 'stimul':62 'sure':80 'syntax':204 'take':179 'time':117,119 'ton':51 'turn':10 'tutori':24,68 'type':72 'video':77 'way':66,170 'webpack':197
```

---
transition: fade-out
---

# Tahap 3: Tahap Pencarian (Search Stage)

Untuk setiap subtopik, sistem melakukan dua jenis pencarian secara paralel:
* **Similarity Search (Semantic Search)**
    * Menggunakan *cosine similarity* antara *embedding vector* subtopik dengan *embedding vector* dari kursus, *chapter*, dan item kurikulum.
    * Pencarian ini menangkap kesamaan semantik dan dapat menemukan konten yang relevan meskipun tidak menggunakan kata kunci yang sama persis.
* **Full-text Search (Keyword Search)**
    * Menggunakan *PostgreSQL full-text search* dengan TSQuery yang telah dibentuk.
    * Pencarian ini menangkap kesamaan leksikal dan sangat efektif untuk menemukan konten dengan kata kunci yang spesifik.

---
transition: fade-out
---

# Tahap 4: Ranking dan Hasil

Untuk mempercepat proses rekomendasi, dilakukan pemeringkatan awal yang disimpan dalam *lookup table* di database.
* Hasil dari *keyword search* diambil peringkat dan skor kecocokannya.
* Hasil dari *semantic search* diambil peringkat dan skor kemiripannya.

Jumlah peringkat hasil yang diambil berbeda berdasarkan granularitas dan volume data:
* **Data kursus:** 100 teratas (baik *similarity* maupun *full-text search*).
    * Dari total 21.641 data, 100 item membuat *lookup table* kecil & cepat diakses.
* **Data *chapters*:** 1000 teratas (baik *similarity* maupun *full-text search*).
    * Dari total 178.088 data, 1.000 cukup besar untuk cakupan solid, namun terkendali.
* **Data *curriculum items*:** 5000 teratas (baik *similarity* maupun *full-text search*).
    * Dari total 1.116.290 data, 5.000 hasil teratas meningkatkan peluang secara signifikan untuk menemukan item-item "niche" atau langka yang dicari pengguna.

---
transition: fade-out
---

# Tahap 5: Penyimpanan (Storage)

Hasil pencarian kemudian disimpan dalam enam *lookup table* terpisah:
* `top_courses_by_similarity` (subtopic_id, course_id, score, rank)
* `top_courses_by_score` (subtopic_id, course_id, score, rank)
* `top_chapters_by_similarity` (subtopic_id, course_id, chapter_id, score, rank)
* `top_chapters_by_score` (subtopic_id, course_id, chapter_id, score, rank)
* `top_curriculum_items_by_similarity` (subtopic_id, chapter_id, curriculum_item_id, score, rank)
* `top_curriculum_items_by_score` (subtopic_id, chapter_id, curriculum_item_id, score, rank)

---
transition: fade-out
---

# Perancangan Algoritma

<img src="./alur1.png" alt="Perancangan Algoritma" class="h-100">

---
transition: fade-out
---

# Perancangan Algoritma

Sistem rekomendasi mengimplementasikan pendekatan *multi-level ranking* yang menggabungkan dua metode utama:
* *Score-based ranking* (hasil dari *full-text search* / *keyword search*)
* *Similarity-based ranking* (hasil dari *vector search* / *semantic search*)

Algoritma ini menggunakan teknik Reciprocal Rank Fusion (RRF) untuk mengintegrasikan berbagai sinyal *ranking* pada tiga tingkat hierarki yang berbeda:
* *Course level*
* *Chapter level*
* *Curriculum item level*

---
layout: default
transition: fade-out
---

# Input dan Preprocessing

* Sistem menerima dua parameter utama:
    * `subtopicId`: ID dari subtopik yang menjadi basis rekomendasi.
    * `numRecommendations`: Jumlah rekomendasi kursus yang diinginkan.
* Tahap *preprocessing* melakukan validasi keberadaan subtopik dalam database. Jika subtopik tidak ditemukan, sistem akan mengembalikan *error* untuk mencegah proses yang tidak valid.

---
transition: fade-out
---

# Pengambilan Data Dua Metode

Sistem mengimplementasikan pendekatan dua metode untuk mengumpulkan kandidat kursus:

### a. Metode Berbasis Skor (*Score-based method*)
Metode ini mengambil data berdasarkan skor relevansi dengan subtopik yang sudah diperhitungkan sebelumnya:
* `TopCoursesByScore`: Kursus dengan skor relevansi tertinggi.
* `TopChaptersByScore`: *Chapter* dengan skor relevansi tertinggi.
* `TopCurriculumItemsByScore`: Item kurikulum dengan skor relevansi tertinggi.

### b. Metode Berbasis Kesamaan (*Similarity-based method*)
Metode ini mengambil data berdasarkan kemiripan konten dengan subtopik target:
* `TopCoursesBySimilarity`: Kursus dengan tingkat kesamaan tertinggi.
* `TopChaptersBySimilarity`: *Chapter* dengan skor relevansi tertinggi.
* `TopCurriculumItemsBySimilarity`: Item kurikulum dengan skor relevansi tertinggi.

---
transition: fade-out
---

# Algoritma Pemeringkatan Multi-level

<img src="./alur2.png" alt="Algoritma Pemeringkatan Multi-level" class="h-100">

---
transition: fade-out
---

# Algoritma Pemeringkatan Multi-level

Setiap metode (*score-based* dan *similarity-based*) diproses menggunakan algoritma *ranking multi-level* yang sama dengan tahapan sebagai berikut:

### a. Pembentukan Struktur *Map* untuk Kursus
* Sistem membuat struktur data *map* yang memetakan setiap kursus dengan komponen-komponennya (*chapter* dan *curriculum item*).

### b. Pemrosesan Data secara Hierarkis
* Kursus yang langsung terkait dengan subtopik dimasukkan ke dalam *map*.
* *Chapter* yang relevan dikelompokkan berdasarkan kursus induknya.
* Item kurikulum diagregasi ke dalam *chapter* dan kursus yang sesuai.

### c. Perhitungan Reciprocal Rank Fusion (RRF)
* Untuk setiap kursus, sistem menghitung skor RRF.

---
transition: fade-out
---

# Contoh Skor RRF Sementara (Keyword Search)

Berikut 5 peringkat kursus teratas berdasarkan perhitungan skor RRF sementara menggunakan skor dari *keyword search*:

| Peringkat Akhir | ID Kursus | Peringkat Awal | Jumlah Bab | Jumlah Item Kur. | Skor RRF |
|---|---|---|---|---|---|
| 1 | 1015110 | 3 | 1 | 1 | 0.02483 |
| 2 | 4415798 | 1 | 3 | 9 | 0.02257 |
| 3 | 4462642 | 23 | 1 | 6 | 0.02244 |
| 4 | 2035846 | 4 | 3 | 9 | 0.02168 |
| 5 | 1527300 | 12 | 1 | 1 | 0.01875 |

**Catatan:** Kursus dengan ID 4462642 yang memiliki peringkat awal 23, naik ke peringkat 3 karena memiliki bab dan item kurikulum yang lebih relevan.

---
transition: fade-out
---

# Contoh Skor RRF Sementara (Semantic Search)

Berikut 5 peringkat kursus teratas berdasarkan perhitungan skor RRF sementara menggunakan nilai *similarity* dari *semantic search*:

| Peringkat Akhir | ID Kursus | Peringkat Awal | Jumlah Bab | Jumlah Item Kur. | Skor RRF |
|---|---|---|---|---|---|
| 1 | 2444060 | 3 | 1 | 2 | 0.02699 |
| 2 | 3920936 | 1 | 1 | 8 | 0.02325 |
| 3 | 2334226 | 36 | 1 | 2 | 0.02171 |
| 4 | 4484690 | 47 | 1 | 1 | 0.02135 |
| 5 | 4984226 | 15 | 2 | 2 | 0.01942 |

**Catatan:** Kursus dengan ID 4484690 yang memiliki peringkat awal 47, naik ke peringkat 4 karena memiliki bab dan item kurikulum yang lebih relevan.

---
transition: fade-out
---

# Penggabungan Peringkat

* Kedua hasil *ranking* (*score-based* dan *similarity-based*) digabungkan menggunakan pendekatan *weighted RRF*.
* Skor akhir dihitung menggunakan persamaan yang telah ditentukan.

**Proses:**
* Sistem memiliki dua daftar peringkat: satu dari alur *score-based* dan satu lagi dari alur *similarity-based*.
* Kedua daftar ini digabungkan sekali lagi menggunakan RRF untuk menghasilkan satu peringkat akhir yang komprehensif.
* Bobot: `scoreWeight = 0.5`, `similarityWeight = 0.5`.

---
transition: fade-out
---

# Contoh Perhitungan Skor Gabungan

**Untuk ID Kursus 5080008:**
* Peringkat dari daftar *score-based* (`scoreRank`): 9
* Peringkat dari daftar *similarity-based* (`similarityRank`): 20

* **Kontribusi skor:** `0.5 * (1 / (60 + 9)) = 0.00724`
* **Kontribusi *similarity*:** `0.5 * (1 / (60 + 20)) = 0.00625`
* **Skor Gabungan:** `0.00724 + 0.00625 = 0.01349`

Setelah dihitung untuk semua kursus, kursus 5080008 menempati peringkat pertama di daftar gabungan.

---
transition: fade-out
---

# Hasil Final Rekomendasi

* Semua kursus diurutkan berdasarkan `combined score` dari yang terbesar ke yang terkecil untuk mendapatkan peringkat final.
* Sistem kemudian mengambil informasi lengkap kursus dari database yang mencakup kategori, label, instruktur, serta struktur *chapter* dan *curriculum item*.
* *Output* kemudian dibatasi sesuai dengan parameter `numRecommendations` yang diminta.

---
transition: fade-out
---
# Implementasi

<img src="./implementasi.png" alt="Implementasi" class="h-100">
<a href="https://course-compass.dalhaqq.my.id" target="_blank">course-compass.dalhaqq.my.id</a>

---
transition: fade-out
---
# Pengujian Fungsional dengan Cypress

<iframe src="http://localhost:5500/course-compass-new/cypress/reports/html/index.html" width="100%" height="85%"></iframe>

---
transition: fade-out
---
# Evaluasi Hasil Rekomendasi dengan Metrik Precision@K

<iframe src="http://localhost:3000" width="100%" height="85%"></iframe>

---
layout: cover
background: https://cover.sli.dev
---

# BAB V
## PENUTUP

---
transition: fade-out
---

# Kesimpulan
Berdasarkan hasil penelitian dalam pengembangan sistem rekomendasi kursus pemrograman online berbasis roadmap pembelajaran, dapat disimpulkan bahwa:

* Sistem rekomendasi berhasil mengintegrasikan roadmap pembelajaran *frontend* dan *backend developer* dengan mengadopsi struktur hierarkis dari situs roadmap.sh yang terdiri dari topik dan subtopik berurutan, kemudian menghubungkannya dengan data kursus Udemy berdasarkan progres pembelajaran pengguna.

 Hasil *end-to-end testing* menggunakan Cypress menunjukkan *passing rate* 100%, membuktikan sistem dapat memberikan rekomendasi terstruktur sesuai alur pembelajaran.


* Implementasi pendekatan gabungan dilakukan dengan menggabungkan *full-text search* dan *text similarity* menggunakan algoritma *multi-level ranking* pada tiga tingkat hierarki, yang kemudian diintegrasikan melalui *weighted Reciprocal Rank Fusion* untuk menghasilkan skor akhir rekomendasi.

Pendekatan ini terbukti efektif dengan nilai metrik P@5 sebesar 0.647 dan P@10 sebesar 0.601, menunjukkan peningkatan signifikan dibandingkan metode tunggal dan mencapai tingkat presisi yang memadai untuk aplikasi praktis sistem rekomendasi kursus.


---
transition: fade-out
---

# Saran

Beberapa saran untuk pengembangan lebih lanjut:

* **Perluasan Cakupan Data:** Menambahkan platform pembelajaran online lainnya seperti Coursera, edX, atau Khan Academy untuk variasi rekomendasi yang lebih beragam.
* **Penyempurnaan Model Embedding:** Melakukan *fine-tuning* pada model *embedding* agar hasil pencarian semantik lebih akurat.
* **Personalisasi Lebih Lanjut:** Mengintegrasikan sistem dengan riwayat pembelajaran pengguna, preferensi tingkat kesulitan, dan *feedback* untuk menghasilkan rekomendasi yang lebih personal.

---
layout: center
class: text-center
---

# Pertanyaan dan Saran

---
layout: center
class: text-center
---

# Terima Kasih

<PoweredBySlidev mt-10 />
