<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>TAMU Digital Content Accessibility Decision Tree</title>
  <style>
    :root {
      --tamu-maroon: #500000;
      --tamu-maroon-dark: #3c0000;
      --bg-light: #f8f9fa;
      --border-color: #d1d5db;
      --text-dark: #1f2937;
      --warning-bg: #fff3cd;
      --warning-border: #ffc107;
      --warning-text: #664d03;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      background-color: #ffffff;
      color: var(--text-dark);
      line-height: 1.6;
      margin: 0;
      padding: 20px;
    }

    .container {
      max-width: 800px;
      margin: 0 auto;
    }

    header {
      border-bottom: 3px solid var(--tamu-maroon);
      padding-bottom: 12px;
      margin-bottom: 24px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
    }

    h1 {
      color: var(--tamu-maroon);
      font-size: 1.5rem;
      margin: 0;
    }

    .reset-btn {
      background-color: #ffffff;
      color: var(--tamu-maroon);
      border: 2px solid var(--tamu-maroon);
      padding: 8px 16px;
      font-size: 0.9rem;
      font-weight: 600;
      border-radius: 6px;
      cursor: pointer;
      transition: all 0.2s;
    }

    .reset-btn:hover, .reset-btn:focus {
      background-color: var(--tamu-maroon);
      color: #ffffff;
    }

    .step-card {
      background-color: var(--bg-light);
      border: 1px solid var(--border-color);
      border-left: 6px solid var(--tamu-maroon);
      border-radius: 8px;
      padding: 20px;
      margin-bottom: 20px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.05);
      animation: fadeIn 0.3s ease-in-out;
    }

    .step-card.completed {
      border-left-color: #6b7280;
      opacity: 0.85;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(8px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .step-badge {
      display: inline-block;
      background-color: var(--tamu-maroon);
      color: #ffffff;
      font-size: 0.75rem;
      font-weight: bold;
      text-transform: uppercase;
      padding: 3px 10px;
      border-radius: 12px;
      margin-bottom: 8px;
      letter-spacing: 0.5px;
    }

    h2 {
      margin: 0 0 12px 0;
      font-size: 1.2rem;
      color: #111827;
    }

    .btn-group {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 16px;
    }

    .choice-btn {
      background-color: #ffffff;
      color: var(--text-dark);
      border: 2px solid var(--tamu-maroon);
      padding: 10px 18px;
      font-size: 1rem;
      font-weight: 600;
      border-radius: 6px;
      cursor: pointer;
      transition: all 0.2s;
    }

    .choice-btn:hover, .choice-btn:focus {
      background-color: var(--tamu-maroon);
      color: #ffffff;
    }

    .choice-btn.selected {
      background-color: var(--tamu-maroon);
      color: #ffffff;
    }

    .helper-box {
      background-color: #ffffff;
      border: 1px solid var(--border-color);
      padding: 12px 16px;
      border-radius: 6px;
      margin-top: 14px;
      font-size: 0.95rem;
    }

    .warning-box {
      background-color: var(--warning-bg);
      border: 1px solid #ffecb5;
      border-left: 5px solid var(--warning-border);
      color: var(--warning-text);
      padding: 16px;
      border-radius: 6px;
      margin-top: 16px;
    }

    .warning-box h3 {
      margin-top: 0;
      font-size: 1.05rem;
    }

    a {
      color: #0056b3;
      font-weight: 500;
    }

    a:focus, button:focus {
      outline: 3px solid #2563eb;
      outline-offset: 2px;
    }

    .hidden {
      display: none;
    }
  </style>
</head>
<body>

<div class="container">
  <header>
    <h1>Digital Content Accessibility Decision Tree</h1>
    <button type="button" class="reset-btn" onclick="resetTree()">↻ Start Over</button>
  </header>

  <main id="workflow-container" aria-live="polite">
    
    <!-- STEP 1 -->
    <section class="step-card" id="step-1">
      <span class="step-badge">Step 1</span>
      <h2>Is this material essential for student understanding or success in the course?</h2>
      
      <div class="helper-box">
        <strong>Questions to consider:</strong>
        <ul style="margin: 6px 0 0 0;">
          <li>Could this content be streamlined or replaced with an already accessible resource?</li>
          <li>Would students benefit more from a simplified or updated version of this content?</li>
          <li>Is this content already covered in other course resources?</li>
        </ul>
      </div>

      <div class="btn-group" role="group" aria-label="Step 1 choices">
        <button type="button" class="choice-btn" onclick="selectChoice('step-1', this, 'step-2')">✅ Yes, it is essential</button>
        <button type="button" class="choice-btn" onclick="selectChoice('step-1', this, 'outcome-remove')">❌ No, not essential</button>
      </div>
    </section>

    <!-- OUTCOME: REMOVE -->
    <section class="step-card hidden" id="outcome-remove">
      <span class="step-badge">Action Needed</span>
      <h2>Remove or Replace the Material</h2>
      <p>Since this material is not essential for student understanding or success, <strong>remove it from the course</strong> or replace it with existing accessible material.</p>
    </section>

    <!-- STEP 2 -->
    <section class="step-card hidden" id="step-2">
      <span class="step-badge">Step 2</span>
      <h2>Is the content already available in an accessible format elsewhere?</h2>
      <div class="btn-group" role="group" aria-label="Step 2 choices">
        <button type="button" class="choice-btn" onclick="selectChoice('step-2', this, 'outcome-link')">✅ Yes, available elsewhere</button>
        <button type="button" class="choice-btn" onclick="selectChoice('step-2', this, 'step-3')">❌ No, I need to remediate it</button>
      </div>
    </section>

    <!-- OUTCOME: LINK -->
    <section class="step-card hidden" id="outcome-link">
      <span class="step-badge">Action Needed</span>
      <h2>Link Directly to the Accessible Resource</h2>
      <p>Instead of uploading a duplicate file, link students directly to the existing accessible resource.</p>
      <ul>
        <li>Resource Guide: <a href="#">TAMU Knowledge Base - Accessibility - Linking to external digital resources</a></li>
      </ul>
    </section>

    <!-- STEP 3 -->
    <section class="step-card hidden" id="step-3">
      <span class="step-badge">Step 3</span>
      <h2>Identify the File Type</h2>
      <p>Select the format of your course material to see the specific remediation steps:</p>
      <div class="btn-group" role="group" aria-label="File type choices">
        <button type="button" class="choice-btn" onclick="selectChoice('step-3', this, 'step-4')">Word, PowerPoint, or Canvas Page</button>
        <button type="button" class="choice-btn" onclick="selectChoice('step-3', this, 'step-5')">PDF</button>
        <button type="button" class="choice-btn" onclick="selectChoice('step-3', this, 'step-6')">Video</button>
        <button type="button" class="choice-btn" onclick="selectChoice('step-3', this, 'outcome-other')">Other Format</button>
      </div>
    </section>

    <!-- OUTCOME: OTHER -->
    <section class="step-card hidden" id="outcome-other">
      <span class="step-badge">Action Needed</span>
      <h2>Contact Academic Technology</h2>
      <p>For specialized or uncommon file formats, please reach out to <strong>Academic Technology</strong> for personalized remediation assistance.</p>
    </section>

    <!-- STEP 4: OFFICE / CANVAS -->
    <section class="step-card hidden" id="step-4">
      <span class="step-badge">Step 4: Word, PowerPoint, or Canvas Page</span>
      <h2>Remediate Using Built-in Checkers & Ally/Panorama</h2>
      <ol>
        <li><strong>Use the built-in Accessibility Checker</strong> (Word, PowerPoint, or Canvas) to remediate and re-upload:
          <ul>
            <li><a href="#">TAMU Knowledge Base - Accessibility - How to use the Microsoft Word accessibility checker</a></li>
            <li><a href="#">TAMU Knowledge Base - Accessibility - How to use the PowerPoint accessibility checker</a></li>
            <li><a href="#">TAMU Knowledge Base - Accessibility - Descriptive hyperlinks</a></li>
          </ul>
        </li>
        <li style="margin-top: 10px;"><strong>Use Ally/Panorama</strong> to identify further issues. Remediate and re-upload until resolved, or contact Academic Technology:
          <ul>
            <li><a href="#">Ally Remediation Guide</a> — <em>Important: Do not remediate alt text in Ally (it does not carry over in future courses). Use the Canvas page editor or Panorama to add/edit alt text.</em></li>
            <li><a href="#">Panorama Resource Guide</a></li>
          </ul>
        </li>
      </ol>
    </section>

    <!-- STEP 5: PDF QUESTION 1 -->
    <section class="step-card hidden" id="step-5">
      <span class="step-badge">Step 5: PDFs</span>
      <h2>Do you have the original source file (Word or PowerPoint)?</h2>
      <div class="btn-group" role="group" aria-label="PDF source file choices">
        <button type="button" class="choice-btn" onclick="selectChoice('step-5', this, 'step-5-source-yes')">✅ Yes, I have the source file</button>
        <button type="button" class="choice-btn" onclick="selectChoice('step-5', this, 'step-5-text-check')">❌ No, I only have the PDF</button>
      </div>
    </section>

    <!-- STEP 5A: SOURCE YES -->
    <section class="step-card hidden" id="step-5-source-yes">
      <span class="step-badge">Action Needed</span>
      <h2>Update the Source File & Re-export</h2>
      <p>It is much easier to fix accessibility issues in the original document! Update your Word or PowerPoint file using the steps below, then export it as a brand-new accessible PDF:</p>
      <div class="btn-group">
        <button type="button" class="choice-btn" onclick="selectChoice('step-5-source-yes', this, 'step-4')">View Step 4 Instructions →</button>
      </div>
    </section>

    <!-- STEP 5B: TEXT SELECTABLE CHECK -->
    <section class="step-card hidden" id="step-5-text-check">
      <span class="step-badge">Step 5 (Continued)</span>
      <h2>Can you highlight/select the text on the PDF page with your cursor?</h2>
      <div class="btn-group" role="group" aria-label="PDF selectable text choices">
        <button type="button" class="choice-btn" onclick="selectChoice('step-5-text-check', this, 'step-5-remediate')">✅ Yes, text is selectable</button>
        <button type="button" class="choice-btn" onclick="selectChoice('step-5-text-check', this, 'step-5-scanned')">❌ No (it's a scanned image)</button>
      </div>
    </section>

    <!-- STEP 5C: SCANNED PDF -->
    <section class="step-card hidden" id="step-5-scanned">
      <span class="step-badge">Action Needed</span>
      <h2>Recreate the Content or Contact Support</h2>
      <p>Because the text cannot be selected, screen readers see this PDF as a blank image. Consider <strong>recreating the content in an accessible format</strong> (such as a Canvas page or Word document) or <strong>contact Academic Technology</strong> for OCR/remediation help.</p>
    </section>

    <!-- STEP 5D: PDF REMEDIATION -->
    <section class="step-card hidden" id="step-5-remediate">
      <span class="step-badge">Steps to Remediate PDF</span>
      <h2>Remediate in Adobe Acrobat Pro & Ally/Panorama</h2>
      <ol>
        <li><strong>Use Adobe Acrobat Pro's built-in Accessibility Checker</strong> to remediate and re-upload:
          <ul>
            <li><a href="#">TAMU Center for Teaching Excellence PDF Remediation Guide</a></li>
          </ul>
        </li>
        <li style="margin-top: 10px;"><strong>Use Ally/Panorama</strong> to identify remaining issues. Remediate and re-upload until resolved (if remaining issues involve tags or table headings, please contact Academic Technology):
          <ul>
            <li><a href="#">Ally Remediation Guide</a></li>
            <li><a href="#">Panorama Resource Guide</a></li>
          </ul>
        </li>
      </ol>

      <aside class="warning-box" role="note">
        <h3>⚠️ NOTE: Do NOT use the Document Reference tool on PDFs</h3>
        <p>While Ally shows a score increase when a Document Reference is added, this creates a <strong>"false sense of accessibility."</strong> The underlying PDF remains inaccessible to students using screen readers.</p>
        <ul style="margin-bottom: 0;">
          <li><strong>Audit Risk:</strong> A Document Reference does not satisfy legal requirements in an audit.</li>
          <li><strong>Student Experience:</strong> Masking the issue hides the warning icon for the instructor without removing the barrier for the student.</li>
        </ul>
      </aside>
    </section>

    <!-- STEP 6: VIDEOS -->
    <section class="step-card hidden" id="step-6">
      <span class="step-badge">Step 6: Videos</span>
      <h2>Video Captioning & Transcripts</h2>
      <p>At this time, we are still gathering information from the university regarding expectations for captioning and transcripts for videos. Here is what we know so far:</p>
      <ul>
        <li><strong>Review Auto-Captions:</strong> Auto-generated captions (like those on YouTube and Vimeo) are often not sufficient unless reviewed and corrected for accuracy.</li>
        <li><strong>Inspect Video Elements:</strong> Use accessibility checkers or browser extensions (like WAVE or Accessibility Insights) to inspect video elements.</li>
        <li><strong>Resource:</strong> <a href="#">TAMU Knowledge Base - Accessibility - Transcripts and captions</a></li>
        <li><strong>Platform Update:</strong> Captioning with Mediasite is going away — please replace Mediasite links with <strong>Panopto</strong> links.</li>
      </ul>
    </section>

  </main>
</div>

<script>
  // Tracks the active path of card IDs so branching back works cleanly
  let activePath = ['step-1'];

  function selectChoice(currentCardId, buttonElement, nextCardId) {
    const currentIndex = activePath.indexOf(currentCardId);
    
    // Hide any cards that were opened after the current card (in case user changes their mind)
    if (currentIndex !== -1) {
      const cardsToHide = activePath.slice(currentIndex + 1);
      cardsToHide.forEach(id => {
        const el = document.getElementById(id);
        if (el) {
          el.classList.add('hidden');
          el.classList.remove('completed');
          // Reset button states inside hidden cards
          el.querySelectorAll('.choice-btn').forEach(btn => btn.classList.remove('selected'));
        }
      });
      activePath = activePath.slice(0, currentIndex + 1);
    }

    // Highlight the selected button in the current card
    const currentCard = document.getElementById(currentCardId);
    currentCard.querySelectorAll('.choice-btn').forEach(btn => btn.classList.remove('selected'));
    buttonElement.classList.add('selected');
    currentCard.classList.add('completed');

    // Reveal the next card
    const nextCard = document.getElementById(nextCardId);
    if (nextCard) {
      nextCard.classList.remove('hidden');
      activePath.push(nextCardId);
      
      // Smoothly scroll the new step into view
      nextCard.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
    }
  }

  function resetTree() {
    activePath.forEach((id, index) => {
      const el = document.getElementById(id);
      if (el) {
        el.classList.remove('completed');
        el.querySelectorAll('.choice-btn').forEach(btn => btn.classList.remove('selected'));
        if (index > 0) {
          el.classList.add('hidden');
        }
      }
    });
    activePath = ['step-1'];
    document.getElementById('step-1').scrollIntoView({ behavior: 'smooth', block: 'nearest' });
  }
</script>

</body>
</html>
