# Indian Speech ASR Template Testing Guide

## 🎵 **Audio Annotation Template Overview**

### **Key Components Explained:**

1. **`<Audio>` Player**:
   - Waveform visualization for precise segment selection
   - Speed control for difficult speech
   - Zoom functionality for detailed annotation
   - Hotkey support (Ctrl+Enter for play/pause)

2. **Language Labels**:
   - Hindi, Marathi, Hinglish, English, Mixed
   - Color-coded for quick identification
   - Hotkeys: h, m, g, e, x

3. **Segment-based Transcription**:
   - `perRegion="true"` enables transcription per audio segment
   - Supports Unicode (Devanagari script)
   - Required field ensures data quality

4. **Quality Metrics**:
   - Audio quality rating (1-5 stars)
   - Speech characteristics (Clear, Noisy, etc.)
   - Transcription confidence (1-3 scale)

## 🧪 **MANDATORY TESTING CHECKLIST**

### **Step 1: Prepare Test Audio Data**

**Sample JSON format**:
```json
[
  {
    "audio": "https://example.com/hindi_speech.wav"
  },
  {
    "audio": "/path/to/local/marathi_audio.mp3"
  },
  {
    "audio": "file:///C:/audio/hinglish_conversation.wav"
  }
]
```

**Supported Audio Formats**:
- WAV, MP3, OGG, M4A, FLAC
- Recommended: WAV 16kHz mono for best performance

### **Step 2: Template Verification**

✅ **Check template appears in**:
- Category: "India-Specific"
- Name: "Indian Speech ASR (Multi-Language)"
- Description mentions Hindi, Marathi, Hinglish

### **Step 3: Audio Interface Testing**

#### **A. Audio Player Controls**
- [ ] Audio loads and plays correctly
- [ ] Waveform displays properly
- [ ] Zoom in/out works on waveform
- [ ] Speed control works (0.5x, 1x, 2x)
- [ ] Volume control functional
- [ ] Play/pause with Ctrl+Enter hotkey

#### **B. Segment Selection**
- [ ] Can select audio regions by clicking and dragging on waveform
- [ ] Multiple segments can be created
- [ ] Segments can be resized and moved
- [ ] Segment boundaries are precise

#### **C. Language Classification**
- [ ] 5 language labels visible with colors
- [ ] Hotkeys work: h(Hindi), m(Marathi), g(Hinglish), e(English), x(Mixed)
- [ ] Labels can be applied to segments
- [ ] Multiple segments can have different languages

### **Step 4: Transcription Testing**

#### **A. Text Input**
- [ ] Text area appears for each audio segment
- [ ] Placeholder text shows script examples
- [ ] Unicode input works (test: हिंदी, मराठी)
- [ ] Required validation prevents empty submissions

#### **B. Multi-script Support**
Test with these sample texts:
- **Hindi**: "नमस्ते, आप कैसे हैं?"
- **Marathi**: "नमस्कार, तुम्ही कसे आहात?"
- **Hinglish**: "Hi, main office जा रहा हूं"
- **English**: "Hello, how are you today?"

### **Step 5: Quality Assessment**

#### **A. Rating Systems**
- [ ] Audio quality: 5-star rating per segment
- [ ] Transcription confidence: 3-level rating
- [ ] Hotkey 'q' works for quality rating

#### **B. Classification Dropdowns**
- [ ] Accent: Urban/Rural/Regional/Neutral
- [ ] Speaker info: Male/Female/Child/etc.
- [ ] Speech quality: Clear/Noisy/Fast/etc.
- [ ] Code-switching: None/Word Level/Phrase Level/etc.

### **Step 6: Complete Workflow Test**

**Full annotation process**:
1. **Load audio** with mixed Hindi-English speech
2. **Select first segment** (Hindi portion)
3. **Apply "Hindi" label** (hotkey: h)
4. **Transcribe in Devanagari**: "हैलो, मैं ठीक हूं"
5. **Rate audio quality** (e.g., 4 stars)
6. **Set accent** to "Urban"
7. **Select second segment** (English portion)
8. **Apply "English" label** (hotkey: e)
9. **Transcribe**: "How are you doing today?"
10. **Submit annotation**

✅ **Success criteria**: All data saves without errors

### **Step 7: Export Validation**

**Export as JSON and verify structure**:
```json
{
  "annotations": [
    {
      "result": [
        {
          "value": {
            "start": 0.5,
            "end": 3.2,
            "labels": ["Hindi"],
            "transcription": "हैलो, मैं ठीक हूं",
            "audio_quality": 4,
            "accent": "Urban"
          }
        }
      ]
    }
  ]
}
```

## 🎯 **Indian Speech Dataset Applications**

### **Training Data Generation**:
- **ASR Models**: Hindi/Marathi speech recognition
- **Accent Classification**: Urban vs Rural speech patterns
- **Code-switching Detection**: Hinglish language models
- **Quality Assessment**: Audio preprocessing pipelines

### **Research Applications**:
- Multilingual speech processing
- Indian accent recognition
- Code-switching analysis
- Regional dialect studies

## 🔧 **Troubleshooting**

### **Audio not loading?**
- Check file format (WAV/MP3 recommended)
- Verify file path accessibility
- Test with smaller audio files first
- Check browser audio codec support

### **Waveform not displaying?**
- Enable browser audio permissions
- Try different browser (Chrome recommended)
- Check for JavaScript console errors
- Ensure audio file is not corrupted

### **Unicode text issues?**
- Verify browser font support for Devanagari
- Test input method editor (IME) setup
- Check database UTF-8 encoding
- Try copy-paste from external source

### **Segment selection problems?**
- Click and drag on waveform area
- Ensure audio is fully loaded before selecting
- Try zooming in for precise selection
- Check if audio duration is reasonable

## 📊 **Sample Test Data Sources**

**For comprehensive testing**:
- **Hindi**: News broadcasts, movie dialogues
- **Marathi**: Regional news, folk songs
- **Hinglish**: Call center recordings, casual conversations
- **Mixed**: Bollywood songs, social media videos

**Audio characteristics to test**:
- Clear studio recordings
- Phone call quality
- Background noise scenarios
- Multiple speaker conversations
- Fast/slow speech patterns

## 🎓 **Academic Project Value**

This template enables:
- **Multilingual Dataset Creation**: Hindi/Marathi/Hinglish corpus
- **Accent Analysis**: Urban vs Rural speech patterns
- **Code-switching Research**: Language mixing patterns
- **Quality Control**: Systematic audio annotation
- **Scalable Annotation**: Production-ready workflow

Perfect for academic research in Indian speech processing and multilingual ASR systems!