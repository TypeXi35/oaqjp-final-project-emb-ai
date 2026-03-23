import unittest
from EmotionDetection.emotion_detection import emotion_detector

class TestEmotionDetection(unittest.TestCase):
    def test_joy(self):
        test_text = emotion_detector("I am glad this happened")
        test_dominant = test_text.get('dominant_emotion')
        self.assertEqual(test_dominant, "joy")

    def test_anger(self):
        test_text = emotion_detector("I am really mad about this")
        test_dominant = test_text.get('dominant_emotion')
        self.assertEqual(test_dominant, "anger")
    
    def test_disgust(self):
        test_text = emotion_detector("I feel disgusted just hearing about this")
        test_dominant = test_text.get('dominant_emotion')
        self.assertEqual(test_dominant, "disgust")

    def test_sadness(self):
        test_text = emotion_detector("I am so sad about this")
        test_dominant = test_text.get('dominant_emotion')
        self.assertEqual(test_dominant, "sadness")

    def test_fear(self):
        test_text = emotion_detector("I am really afraid that this will happen")
        test_dominant = test_text.get('dominant_emotion')
        self.assertEqual(test_dominant, "fear")

if __name__ == '__main__':
    unittest.main()