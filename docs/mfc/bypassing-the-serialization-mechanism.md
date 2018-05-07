---
title: Pomijanie mechanizmu serializacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a45779034534ce87bd6bd4f55dfda4985a36f01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="bypassing-the-serialization-mechanism"></a>Pomijanie mechanizmu serializacji
Jak już wspomniano, platformę umożliwia domyślne do odczytywania i zapisywania danych do i z plików. Serializacja za pośrednictwem obiektu archiwum odpowiada potrzebom z bardzo wielu aplikacji. Takiej aplikacji odczytuje plik wyłącznie w pamięci, użytkownicy będą mogli zaktualizować pliku, a następnie zapisuje zaktualizowanej wersji na dysku, ponownie.  
  
 Jednak niektóre aplikacje działają na danych bardzo inaczej, a dla tych aplikacji serializacji za pomocą archiwum nie jest odpowiedni. Przykładami bazy danych programów, programy, które edytowanie tylko części dużych plików, programy, które zapisać pliki tekstowe i programy, które współużytkują pliki danych.  
  
 W takich przypadkach można zastąpić [serializacja](../mfc/reference/cobject-class.md#serialize) w inny sposób do pośredniczących plików akcji za pomocą funkcji [cfile —](../mfc/reference/cfile-class.md) obiektu zamiast [CArchive](../mfc/reference/carchive-class.md) obiektu.  
  
 Można użyć **Otwórz**, **odczytu**, **zapisu**, **Zamknij**, i `Seek` funkcji elementów członkowskich klasy `CFile` próbę otwarcia pliku , przenieś wskaźnik pliku (wyszukiwanie) do określonego punktu w pliku, w tym momencie Odczytaj rekord (określoną liczbę bajtów), umożliwiają zaktualizowanie użytkownika rekordu, następnie przejść do tego samego punktu ponownie i zapisu rekordu z powrotem do pliku. Platformę spowoduje otwarcie pliku dla Ciebie i można użyć `GetFile` funkcji członkowskiej klasy `CArchive` uzyskać wskaźnik do `CFile` obiektu. Użyj bardziej zaawansowane i elastyczne, można zastąpić [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) i [OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument) funkcji elementów członkowskich klasy `CWinApp`. Aby uzyskać więcej informacji, zobacz klasy [cfile —](../mfc/reference/cfile-class.md) w *odwołania MFC*.  
  
 W tym scenariuszu sieci `Serialize` zastąpienie nie robi nic, jeśli na przykład chcesz, aby go do odczytu i zapisu nagłówka pliku, aby zachować aktualne po zamknięciu dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie dokumentów](../mfc/using-documents.md)

