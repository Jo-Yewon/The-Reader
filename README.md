# 더 리더 The Reader
 > 더 리더는 시각장애인을 위한 메신저 어플리케이션으로 음성합성(Text-To-Speech)을 통해 사용자가 받은 메시지를 음성으로 들려주고 
 음성인식(Speech-To-Text)을 통해 사용자가 음성으로 말한 내용을 텍스트로 바꿔준다.또 단순한 음성인식 기능에서 더 나아가 음성인식된 키워드를 중심으로
 관련 이모티콘을 전송하여 시각장애인들의 표현의 다양성을 높이면서 더 편리하게 메시지를 주고 받을 수 있도록 제작한 안드로이드 기반의 어플리케이션이다.

# 1.How to use
앱 설치 방법 및 사용법

# 2.주요기능 및 관련코드

2.1 UI
--

2.2 음성합성
--
```javascript
private void readVoiceMessage(final Set<MessageRecord> messageRecords) {
   List<MessageRecord> messageList = new LinkedList<>(messageRecords);
    Collections.sort(messageList, new Comparator<MessageRecord>() {
      @Override
      public int compare(MessageRecord lhs, MessageRecord rhs) {
        if      (lhs.getDateReceived() < rhs.getDateReceived())  return -1;
        else if (lhs.getDateReceived() == rhs.getDateReceived()) return 0;
        else                                                     return 1;
      }
    });

    StringBuilder    bodyBuilder = new StringBuilder();

    for (MessageRecord messageRecord : messageList) {
      String body = messageRecord.getDisplayBody().toString();
      if (!TextUtils.isEmpty(body)) {
        bodyBuilder.append(body).append('\n');
      }
    }
    if (bodyBuilder.length() > 0 && bodyBuilder.charAt(bodyBuilder.length() - 1) == '\n') {
      bodyBuilder.deleteCharAt(bodyBuilder.length() - 1);
    }

    String result = bodyBuilder.toString();

    if (!TextUtils.isEmpty(result))
       tts.speak(result,TextToSpeech.QUEUE_FLUSH,null);
  }
 ```
  
2.3 음성인식
--

2.4 키워드 분류 및 이모티콘 전송
--


## 3.사용한 API
siganl-android https://github.com/youngji-koh/Signal-Android

## 4.개발자 정보
1515003 고영지(youngji-koh) - 사용자 인터페이스 및 음성합성 기능 구현
- Youngji : 글씨 크기 조절 기능 추가, 고대비 테마 추가, 음성합성 기능 구현, 중간 발표자료 담당

1615035 신유진(jellyb3ar) - 음성인식 및 키워드 분류 기능 기능 구현
- jellyb3ar : 음성인식 및 키워드에 따른 이모티콘 전송 기능 구현, 중간 발표자료 담당

1771018 김혜지(kimhj5854) - 음성인식 및 키워드 분류 기능 구현
- Maeg : 음성인식 및 키워드에 따른 이모티콘 전송 기능 구현, 


1771045 이지은(Iamjieun) - 음성인식 및 키워드 분류 담당
-

1771104 조예원(QueenCurry) - 음성합성 기능 및 사용자 인터페이스 구현
- JoYewon : 카카오 앱 키 설정, 음성합성 기능 구현, 글씨 크기 조절 기능 추가, 중간 발표자료 담당


## License

Copyright 2011 Whisper Systems

Copyright 2013-2017 Open Whisper Systems

Licensed under the GPLv3: http://www.gnu.org/licenses/gpl-3.0.html

Google Play and the Google Play logo are trademarks of Google Inc.
