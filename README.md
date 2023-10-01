# MINE24
MODEL
# import os
# import subprocess

# def get_video_transcript(video_path):
#     # Check if closed captioning file exists
#     cc_file = video_path.replace(".mp4", ".srt")
#     if os.path.exists(cc_file):
#         with open(cc_file, 'r') as file:
#             transcript = file.read()
#         return transcript

#     # If closed captioning file doesn't exist, use audio-to-text conversion
#     audio_file = video_path.replace(".mp4", ".wav")
#     subprocess.run(["ffmpeg", "-i", video_path, "-vn", "-ac", "1", "-ar", "16000", audio_file])

#     # Use speech-to-text API to convert audio to text
#     transcript = speech_to_text_conversion(audio_file)

#     # Save transcript as closed captioning file
#     with open(cc_file, 'w') as file:
#         file.write(transcript)

#     # Delete temporary audio file
#     os.remove(audio_file)

#     return transcript

# def speech_to_text_conversion(audio_file):
#     # Use speech-to-text API to convert audio to text
#     # Replace this with the actual speech-to-text conversion code or API call
#     transcript = "This is a sample transcript."

#     return transcript

# if __name__ == "__main__":
#     video_path = "path/to/video.mp4"
#     transcript = get_video_transcript(video_path)
#     print(transcript)
import os
import subprocess

# Function to convert audio to text (you need to replace this with actual implementation)
def speech_to_text_conversion(audio_file):
    # Replace this with the actual speech-to-text conversion code or API call
    transcript = "This is a sample transcript."
    return transcript

def get_video_transcript(video_path):
    # Check if the input video path is valid
    if not os.path.exists(video_path):
        print("Video file not found.")
        return None

    # Check if closed captioning file exists
    cc_file = video_path.replace(".mp4", ".srt")

    if os.path.exists(cc_file):
        with open(cc_file, 'r') as file:
            transcript = file.read()
        return transcript

    # Provide a comment explaining audio-to-text conversion
    print("Converting video to audio...")
    audio_file = video_path.replace(".mp4", ".wav")

    # Use ffmpeg to convert video to audio
    subprocess.run(["ffmpeg", "-i", video_path, "-vn", "-ac", "1", "-ar", "16000", audio_file])

    # Use speech-to-text API to convert audio to text
    print("Converting audio to text...")
    transcript = speech_to_text_conversion(audio_file)

    # Save transcript as closed captioning file
    with open(cc_file, 'w') as file:
        file.write(transcript)

    # Delete temporary audio file
    os.remove(audio_file)

    return transcript

if __name__ == "__main__":
    video_path = "path/to/video.mp4"
    transcript = get_video_transcript(video_path)
    if transcript:
        print("Transcript:")
        print(transcript)

