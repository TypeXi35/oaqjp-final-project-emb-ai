"""
Module for emotion Detection on text
"""
import json
import requests

def emotion_detector(text_to_analyse):
    """
    Runs text through a sentiment analyzer
    Params:
        text_to_analyze: string, Text to be analyzed by the sentiment analyzer
    Returns:
        Dictionary with label and score
            label: string, result of the test Positive / Negative / Neutral
            score: string, score of the test in numerical value
    """
    base_url ='https://sn-watson-emotion.labs.skills.network/v1'
    url = base_url + '/watson.runtime.nlp.v1/NlpService/EmotionPredict'
    
    header = {"grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"}
    
    input_json = { "raw_document": { "text": text_to_analyse } }
    
    response = requests.post(url, json = input_json, headers = header, timeout = 5)
    if response.status_code == 400:
        processed_dict = {
            'anger': None,
            'disgust': None,
            'fear': None,
            'joy': None,
            'sadness': None,
            'dominant_emotion' : None
        }
    else:
        json_response = json.loads(response.text).get("emotionPredictions")[0].get("emotion")
        processed_dict = {
            'anger': json_response.get("anger"),
            'disgust': json_response.get("disgust"),
            'fear': json_response.get("fear"),
            'joy': json_response.get("joy"),
            'sadness': json_response.get("sadness")
        }
        max_value = -1
        max_key = None
        for key in processed_dict:
            if processed_dict[key] > max_value:
                max_value = processed_dict[key]
                max_key = key
        processed_dict['dominant_emotion'] = max_key
    return processed_dict