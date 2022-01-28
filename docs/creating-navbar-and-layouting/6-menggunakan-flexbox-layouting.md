---
sidebar_position: 6
---

# 6. Menggunakan Flexbox Layouting

import useBaseUrl from '@docusaurus/useBaseUrl';

**Flexbox** merupakan mode layout yang ada di **CSS 3** dan digunakan untuk mengatur elemen di suatu halaman web. Flexbox ini akan mengatur ukuran dari elemen anaknya secara otomatis, dan mampu beradaptasi dengan ukuran container-nya.

Tujuan dari flexbox yaitu memberikan container kemampuan untuk mengatur panjang, lebar, dan posisi item-item yang berada di dalamnya agar memaksimalkan ruang yang ada. Pengaturan ini sangat penting bagi seorang frontend developer untuk membuat sebuah website yang nyaman dilihat di berbagai device dengan berbagai macam resolusi.

Flexbox mempunyai sistem koordinat sendiri, yaitu:
- **Main Axis:** garis horizontal yang membentang dari kiri ke kanan (default: row)
- **Cross Axis:** garis vertikal yang membentang dari atas ke bawah (default: column)

<img alt="image1" src={useBaseUrl('img/docs/image-17.png')} height="auto"/>

<div><br /></div>

```html title="contact.html"
<!DOCTYPE html>
<html>
  <head>
    <title>Layouting & Linking</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <!-- NavBar -->
    <nav>
      <div class="left-side">
        <a href="/index.html">
          <img src="assets/logo.png" alt="logo" />
        </a>
        <ul>
          <li>
            <a href="/index.html">Home</a>
          </li>
          <li>
            <a href="#">Blog</a>
          </li>
        </ul>
      </div>
      <div class="right-side">
        <a href="/contact.html"> Contact Me </a>
      </div>
    </nav>

    <!-- Form Contact -->
    <div class="form-contact">
      <div class="container-form">
        <form>
          <div>
            <label for="input-name">Name</label>
            <input id="input-name" type="text" />
          </div>
          <div>
            <label for="input-email">Email</label>
            <input id="input-email" type="text" />
          </div>
          <div>
            <label for="input-phone">Phone Number</label>
            <input id="input-phone" type="text" />
          </div>
          <div>
            <label for="input-subject">Subject</label>
            <select id="input-subject">
              <option value="Privacy Police">Privacy Police</option>
              <option value="Problem With Our Site">
                Problem With Our Site
              </option>
              <option value="Questions on Order">Questions on Order</option>
              <option value="Other Questions">Other Questions</option>
            </select>
          </div>
          <div>
            <label for="message">Your Message</label>
            <textarea id="input-message"></textarea>
          </div>
          <button>Submit</button>
        </form>
      </div>
    </div>
  </body>
</html>
```

```html title="index.html"
<!DOCTYPE html>
<html>
  <head>
    <title>Layouting & Linking</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <!-- NavBar -->
    <nav>
      <div class="left-side">
        <a href="/index.html">
          <img src="assets/logo.png" alt="logo" />
        </a>
        <ul>
          <li>
            <a href="/index.html" class="list-active">Home</a>
          </li>
          <li>
            <a href="#">Blog</a>
          </li>
        </ul>
      </div>
      <div class="right-side">
        <a href="/contact.html"> Contact Me </a>
      </div>
    </nav>

    <!-- Card Profile -->
    <div class="personal">
      <div class="left">
        <div class="card">
          <div class="image">
            <img src="assets/my-img.jpg" alt="my image" />
          </div>
          <div class="header">
            <h1>Rhoma Irama</h1>
          </div>
          <div class="content">
            <p>
              I became a superstar to make awesome app and software to bring new
              life for mankind.
            </p>
            <table border="1">
              <tr>
                <th>Project Name</th>
                <th>Year</th>
              </tr>
              <tr>
                <td>Dumbways Mobile App</td>
                <td>2021</td>
              </tr>
            </table>
          </div>
        </div>
      </div>
      <div class="right">
        <div>
          <h1>What i do</h1>
          <p>
            Lorem Ipsum is simply dummy text of the printing and typesetting
            industry. Lorem Ipsum has been the industry's standard dummy text
            ever since the 1500s, when an unknown printer took a galley of type
            and scrambled it to make a type specimen book. It has survived not
            only five centuries, but also the leap into electronic typesetting,
            remaining essentially unchanged.
          </p>
          <span class="skill">
            <span>
              <img src="assets/js.png" alt="" />
              <h3>Frontend Developer</h3>
              <p>
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsum,
                temporibus.
              </p>
            </span>
            <span>
              <img src="assets/git.png" alt="" />
              <h3>Version Control</h3>
              <p>
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsum,
                temporibus.
              </p>
            </span>
            <span
              ><img src="assets/deploy.png" alt="" />
              <h3>Automated Deployment</h3>
              <p>
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsum,
                temporibus.
              </p>
            </span>
          </span>
          <h1>Found Me on</h1>
          <span class="sosmed-list">
            <a href="facebook.com"
              ><img src="assets/facebook.png" alt="facebook" target="_blank"
            /></a>
            <a href="twitter.com"
              ><img src="assets/twitter.png" alt="twitter" target="_blank"
            /></a>
            <a href="instagram.com"
              ><img src="assets/instagram.png" alt="instagram" target="_blank"
            /></a>
            <a href="mail.com"
              ><img src="assets/mail.png" alt="mail" target="_blank"
            /></a>
            <a href="wa.me/000000000"
              ><img src="assets/whatsapp.png" alt="whatsapp" target="_blank"
            /></a>
          </span>
        </div>
      </div>
    </div>
  </body>
</html>
```
