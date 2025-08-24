---
layout: default
title: Contact
lang: en
permalink: /en/contact/
---

# Get in Touch

I look forward to hearing from you and am happy to offer you a **free 30-minute consultation**. Contact me by phone, email, or use the contact form below.

---

## Contact Information

**📧 Email:** [ar.moltmannwillisch@gmail.com](mailto:ar.moltmannwillisch@gmail.com)  
*Response typically within 24 hours*

**📞 Phone:** [+49 (0) 172 65 29 460](tel:+4917265229460)  
*Mon-Fri 9:00-18:00, WhatsApp also welcome*

**🌐 Website:** [www.moltmann-willisch.de](http://www.moltmann-willisch.de)  
*Additional information and references*

## Contact Form

<div id="success-message" class="success-message" style="display: none;">
  <h3>✅ Message sent successfully!</h3>
  <p>Thank you for your message. I will typically get back to you within 24 hours.</p>
  <button type="button" onclick="showForm()" class="new-message-btn">Send New Message</button>
</div>

<form id="contact-form" class="contact-form" method="POST" action="https://api.web3forms.com/submit">
  <input type="hidden" name="access_key" value="eb558e5f-6473-4b34-836b-fcce0326d612" />
  <input type="hidden" name="subject" value="New message from website (English)" />
  <input type="hidden" name="from_name" value="Mediation Practice Website" />
  <!-- Honeypot for spam protection -->
  <input type="checkbox" name="botcheck" class="hidden" style="display: none;" />
  
  <div class="form-group">
    <label for="name">Name *</label>
    <input type="text" id="name" name="name" required>
  </div>
  
  <div class="form-group">
    <label for="email">Email Address *</label>
    <input type="email" id="email" name="email" required>
  </div>
  
  <div class="form-group">
    <label for="phone">Phone Number</label>
    <input type="tel" id="phone" name="phone">
  </div>
  
  <div class="form-group">
    <label for="subject">Subject</label>
    <select id="subject" name="subject">
      <option value="">Please select a topic</option>
      <option value="mediation">Mediation</option>
      <option value="consultation">Consultation</option>
      <option value="arbitration">Arbitration</option>
      <option value="moderation">Moderation</option>
      <option value="corporate">Corporate Law</option>
      <option value="construction">Construction & Real Estate</option>
      <option value="family">Family & Partnership</option>
      <option value="neighborhood">Neighborhood Disputes</option>
      <option value="organization">Organizations & Associations</option>
      <option value="other">Other</option>
    </select>
  </div>
  
  <div class="form-group">
    <label for="message">Your Message *</label>
    <textarea id="message" name="message" placeholder="Please briefly describe your concern..." required></textarea>
  </div>
  
  <div class="form-group">
    <label>
      <input type="checkbox" name="privacy" required>
      I have read and accept the <a href="{{ "/en/privacy" | relative_url }}">privacy policy</a>. *
    </label>
  </div>
  
  <button type="submit" class="submit-btn">Send Message</button>
</form>

<script>
document.addEventListener('DOMContentLoaded', function() {
    const form = document.getElementById('contact-form');
    const successMessage = document.getElementById('success-message');
    
    if (form) {
        form.addEventListener('submit', async function(e) {
            e.preventDefault();
            
            const submitBtn = form.querySelector('.submit-btn');
            const originalBtnText = submitBtn.textContent;
            
            submitBtn.textContent = 'Sending...';
            submitBtn.disabled = true;
            
            try {
                const formData = new FormData(form);
                const response = await fetch(form.action, {
                    method: 'POST',
                    body: formData
                });
                
                if (response.ok) {
                    form.style.display = 'none';
                    successMessage.style.display = 'block';
                    form.reset();
                } else {
                    throw new Error('Form submission failed');
                }
            } catch (error) {
                alert('There was a problem sending your message. Please try again or contact us directly via email.');
            } finally {
                submitBtn.textContent = originalBtnText;
                submitBtn.disabled = false;
            }
        });
    }
});

function showForm() {
    const form = document.getElementById('contact-form');
    const successMessage = document.getElementById('success-message');
    
    successMessage.style.display = 'none';
    form.style.display = 'block';
    form.scrollIntoView({ behavior: 'smooth' });
}
</script>