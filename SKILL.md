---
name: vertex-image-adc
description: "Generate images via Google Cloud Vertex AI generateContent using Application Default Credentials (ADC)."
homepage: "https://cloud.google.com/vertex-ai"
metadata: {
  "openclaw": {
    "emoji": "🎨",
    "requires": {
      "binaries": ["gcloud", "curl"]
    }
  }
}
---

# Google Cloud Vertex AI Image Generator (ADC)

This skill utilizes the Google Cloud SDK (`gcloud`) and application credentials to call the Google Cloud Vertex AI `generateContent` API, generating images directly using model predictions.

## Workflow

1. Configure required environment variables or parameters:
   - `GOOGLE_CLOUD_PROJECT`: Your Google Cloud Project ID.
   - `GOOGLE_CLOUD_LOCATION` (Optional): Location/region (defaults to `global`).
   - `GOOGLE_CLOUD_MODEL` (Optional): Model name (defaults to `gemini-3.1-flash-image-preview`).
2. Construct/save prompt to a local text file.
3. Call the generation script.

## Commands

### Generate Image (Default ADC)
```bash
python3 {baseDir}/scripts/image_harness.py --prompt-file <prompt_path> --out <output_path>
```

### Advanced Usage
- Specify custom project, location, and model:
```bash
python3 {baseDir}/scripts/image_harness.py --prompt-file <prompt_path> --out <output_path> --project <project_id> --location <location> --model <model>
```
- Use user-auth token instead of ADC:
```bash
python3 {baseDir}/scripts/image_harness.py --prompt-file <prompt_path> --out <output_path> --auth-mode user-token
```

## Setup & Requirements
- Google Cloud SDK (`gcloud` CLI) installed and available in `$PATH`.
- Active authentication token:
  - Default ADC mode: `gcloud auth application-default login`
  - User-token mode: `gcloud auth login`
- The system must have `curl` installed to issue the API request.
