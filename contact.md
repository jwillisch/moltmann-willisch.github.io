---
layout: default
title: Kontakt
permalink: /contact/
---

# Kontakt aufnehmen

Ich freue mich auf Ihre Nachricht und stehe Ihnen gerne für ein **kostenloses 30-minütiges Beratungsgespräch** zur Verfügung. Kontaktieren Sie mich telefonisch, per E-Mail oder nutzen Sie das untenstehende Kontaktformular.

---

## Kontaktdaten

**📧 E-Mail:** [ar.moltmannwillisch@gmail.com](mailto:ar.moltmannwillisch@gmail.com)  
*Antwort in der Regel innerhalb von 24 Stunden*

**📞 Telefon:** [+49 (0) 172 65 29 460](tel:+4917265229460)  
*Mo-Fr 9:00-18:00 Uhr, gerne auch per WhatsApp*

**🌐 Website:** [www.moltmann-willisch.de](http://www.moltmann-willisch.de)  
*Weitere Informationen und Referenzen*

## Kontaktformular

<div id="success-message" class="success-message" style="display: none;">
  <h3>✅ Nachricht erfolgreich gesendet!</h3>
  <p>Vielen Dank für Ihre Nachricht. Ich werde mich in der Regel innerhalb von 24 Stunden bei Ihnen melden.</p>
  <button type="button" onclick="showForm()" class="new-message-btn">Neue Nachricht senden</button>
</div>

<form id="contact-form" class="contact-form" method="POST" action="https://api.web3forms.com/submit">
  <input type="hidden" name="access_key" value="eb558e5f-6473-4b34-836b-fcce0326d612" />
  <input type="hidden" name="subject" value="Neue Nachricht von der Website" />
  <input type="hidden" name="from_name" value="Mediationskanzlei Website" />
  <!-- Honeypot for spam protection -->
  <input type="checkbox" name="botcheck" class="hidden" style="display: none;" />
  
  <div class="form-group">
    <label for="name">Name *</label>
    <input type="text" id="name" name="name" required>
  </div>
  
  <div class="form-group">
    <label for="email">E-Mail-Adresse *</label>
    <input type="email" id="email" name="email" required>
  </div>
  
  <div class="form-group">
    <label for="phone">Telefonnummer</label>
    <input type="tel" id="phone" name="phone">
  </div>
  
  <div class="form-group">
    <label for="subject">Betreff</label>
    <select id="subject" name="subject">
      <option value="">Bitte wählen Sie ein Thema</option>
      <option value="mediation">Mediation</option>
      <option value="beratung">Beratung</option>
      <option value="schlichtung">Schlichtung</option>
      <option value="moderation">Moderation</option>
      <option value="gesellschaftsrecht">Gesellschaftsrecht</option>
      <option value="baurecht">Bauen & Immobilien</option>
      <option value="familie">Familie & Partnerschaft</option>
      <option value="nachbarschaft">Nachbarschaftsstreit</option>
      <option value="verein">Organisation & Verein</option>
      <option value="sonstiges">Sonstiges</option>
    </select>
  </div>
  
  <div class="form-group">
    <label for="message">Ihre Nachricht *</label>
    <textarea id="message" name="message" placeholder="Bitte beschreiben Sie kurz Ihr Anliegen..." required></textarea>
  </div>
  
  <div class="form-group">
    <label>
      <input type="checkbox" name="privacy" required>
      Ich habe die <a href="{{ site.baseurl }}/privacy">Datenschutzerklärung</a> gelesen und akzeptiere diese. *
    </label>
  </div>
  
  <button type="submit" class="submit-btn">Nachricht senden</button>
</form>

## Erstberatung

**Kostenloses Kennenlerngespräch** (30 Minuten)

In einem unverbindlichen Erstgespräch lernen wir uns kennen und ich erhalte einen ersten Eindruck von Ihrer Konfliktsituation. Dabei besprechen wir:

- **Ihre Konfliktsituation** und die beteiligten Parteien
- **Mögliche Verfahrenswege** (Mediation, Schlichtung, Beratung)
- **Ablauf und Dauer** des gewählten Verfahrens
- **Kosten und organisatorische Fragen**

Das Erstgespräch ist für Sie kostenfrei und völlig unverbindlich. Sie entscheiden anschließend, ob Sie mit mir arbeiten möchten.

## Vertraulichkeit

Alle Gespräche und Informationen werden **streng vertraulich** behandelt. Als Mediatorin unterliege ich der gesetzlichen Verschwiegenheitspflicht nach § 4 Mediationsgesetz. 

Ihre Daten werden ausschließlich für die Bearbeitung Ihres Anliegens verwendet und nicht an Dritte weitergegeben.

## Häufig gestellte Fragen

### Wie schnell kann ein Termin stattfinden?
In dringenden Fällen ist oft ein Termin innerhalb weniger Tage möglich. Für eine Mediation sollten Sie etwa 2-3 Wochen für die Vorbereitung einplanen.

### Wo finden die Termine statt?
Je nach Wunsch können Termine in meinen Räumlichkeiten, bei Ihnen vor Ort oder in neutralen Räumen stattfinden. Auch Online-Termine sind möglich.

### Was kostet eine Mediation?
Die Kosten richten sich nach Umfang und Komplexität des Falls. Nach dem Erstgespräch erhalten Sie einen transparenten Kostenvoranschlag.

### Kann eine Mediation scheitern?
Nicht jeder Konflikt ist für eine Mediation geeignet. Die Bereitschaft aller Parteien zur Zusammenarbeit ist Voraussetzung. Sollte keine Einigung möglich sein, haben Sie nichts verloren und können andere Wege beschreiten.

---

Ich freue mich darauf, Sie kennenzulernen und Ihnen bei der Lösung Ihres Konflikts zu helfen!

<script>
document.addEventListener('DOMContentLoaded', function() {
    const form = document.getElementById('contact-form');
    const successMessage = document.getElementById('success-message');
    
    if (form) {
        form.addEventListener('submit', async function(e) {
            e.preventDefault();
            
            const submitBtn = form.querySelector('.submit-btn');
            const originalBtnText = submitBtn.textContent;
            
            // Show loading state
            submitBtn.textContent = 'Wird gesendet...';
            submitBtn.disabled = true;
            
            try {
                const formData = new FormData(form);
                const response = await fetch(form.action, {
                    method: 'POST',
                    body: formData
                });
                
                if (response.ok) {
                    // Hide form and show success message
                    form.style.display = 'none';
                    successMessage.style.display = 'block';
                    
                    // Clear form for next use
                    form.reset();
                } else {
                    throw new Error('Form submission failed');
                }
            } catch (error) {
                alert('Es gab ein Problem beim Senden Ihrer Nachricht. Bitte versuchen Sie es erneut oder kontaktieren Sie uns direkt per E-Mail.');
            } finally {
                // Reset button
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
    
    // Scroll to form
    form.scrollIntoView({ behavior: 'smooth' });
}
</script>