# India-Specific OCR Template Testing Guide

## 🧪 **MANDATORY TESTING CHECKLIST**

### **Step 1: Start Label Studio**
```bash
cd label-studio-develop
python label_studio/manage.py runserver
# OR if installed via pip:
# label-studio start
```

### **Step 2: Create New Project**
1. Open browser: `http://localhost:8080`
2. Click "Create Project"
3. Enter project name: "India OCR Test"
4. Go to "Labeling Interface" tab

### **Step 3: Find Your Template**
✅ **CRITICAL CHECK**: Look for:
- **Template Categories** → "India-Specific" 
- **Template Name** → "India-Specific OCR (Multi-Script)"
- **Description** → "OCR annotation for Indian documents supporting Devanagari and English scripts"

🚨 **If template doesn't appear**:
- Check YAML indentation in config.yml
- Restart Label Studio completely
- Check browser console for errors

### **Step 4: Upload Test Data**

**Sample JSON format for data import**:
```json
[
  {
    "image": "https://example.com/indian_bill.jpg"
  },
  {
    "image": "/path/to/local/receipt.png"
  }
]
```

**OR upload images directly** via UI

### **Step 5: Annotation Interface Validation**

✅ **Must verify ALL these work**:

#### **A. Image Display**
- [ ] Image loads correctly
- [ ] Zoom controls work (+ / - buttons)
- [ ] Pan functionality works (drag image)
- [ ] Rotate controls work

#### **B. Script Labels**
- [ ] 5 script labels visible: Devanagari, English, Mixed, Numeric, Signature
- [ ] Hotkeys work: `d`, `e`, `m`, `n`, `s`
- [ ] Colors display correctly (red, teal, blue, green, yellow)

#### **C. Bounding Box Tool**
- [ ] Can draw rectangles around text
- [ ] Smart adjustment works (snaps to edges)
- [ ] Multiple boxes can be drawn
- [ ] Boxes can be resized/moved

#### **D. Text Transcription**
- [ ] Text area appears for each bounding box
- [ ] Placeholder text shows: "Enter text exactly as shown..."
- [ ] Required validation works (can't submit without text)
- [ ] Supports Unicode (test with: हिंदी, मराठी)

#### **E. Quality Assessment**
- [ ] 5-star rating appears per region
- [ ] Hotkey `q` works for rating
- [ ] Difficulty dropdown works (Clear, Blurry, etc.)

#### **F. Document Type Classification**
- [ ] Document type dropdown appears
- [ ] All options visible: Bill/Invoice, Government Form, etc.

### **Step 6: Complete Annotation Workflow**

1. **Draw bounding box** around Hindi text
2. **Select "Devanagari"** label
3. **Type Hindi text** in transcription field
4. **Rate quality** (1-5 stars)
5. **Mark difficulty** if needed
6. **Submit annotation**

✅ **Success criteria**: Annotation saves without errors

### **Step 7: Export Test**

1. Go to project "Export" tab
2. Export as JSON
3. Verify exported data contains:
   - Bounding box coordinates
   - Script labels
   - Transcribed text
   - Quality ratings

## 📸 **Documentation for Academic Project**

**Take screenshots of**:
1. Template selection screen showing "India-Specific" category
2. Annotation interface with all tools visible
3. Completed annotation with Hindi/English text
4. Exported JSON data structure

## 🔧 **Troubleshooting**

### **Template not appearing?**
```bash
# Check YAML syntax
python -c "import yaml; yaml.safe_load(open('label_studio/annotation_templates/india-specific/indic-ocr/config.yml'))"

# Check Label Studio logs
python label_studio/manage.py runserver --verbosity=2
```

### **Unicode text issues?**
- Ensure browser supports Devanagari fonts
- Test with simple Hindi: हिंदी
- Check database encoding (should be UTF-8)

### **Bounding boxes not working?**
- Check browser console for JavaScript errors
- Try different browser (Chrome recommended)
- Ensure image loads completely before drawing

## 🎯 **Academic Project Value**

This template demonstrates:
- **Multi-script support** for Indian languages
- **Production-ready annotation workflow**
- **Quality control mechanisms**
- **Scalable template architecture**
- **Real-world applicability** for Indian document digitization

## 📊 **Sample Test Data Sources**

For testing, use:
- Indian bills/receipts (with Hindi + English)
- Government forms (mixed script)
- Handwritten notes in Devanagari
- Bank statements with numbers + text

**Remember**: This is MVP-level functionality that can be extended for full production use.