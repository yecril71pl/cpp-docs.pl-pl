---
title: Obsługa MAPI w MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5d6498d1ecb20b47070cb26bf1a9d732340e266
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mapi-support-in-mfc"></a>Obsługa MAPI w MFC
Obsługa podzbioru firmy Microsoft do obsługi komunikatów aplikacji Program interfejsu (MAPI) w klasie dostarcza MFC **CDocument**. W szczególności **CDocument** ma funkcje Członkowskie, które określają, czy obsługa poczty jest obecny na komputerze użytkownika końcowego, a jeśli tak, włącz polecenie Wyślij pocztę o identyfikatorze standardowego polecenia **ID_FILE_SEND_MAIL**. Funkcja Obsługa MFC dla tego polecenia umożliwia użytkownikowi wysłać dokument pocztą e-mail.  
  
> [!TIP]
>  Mimo że MFC nie Hermetyzowanie całego zestawu funkcji MAPI, możesz nadal wywołać funkcji MAPI bezpośrednio, tak jak można wywołać funkcji Win32 API bezpośrednio z programów MFC.  
  
 Dostarczanie poczty wysyłać polecenia w aplikacji jest bardzo proste. MFC udostępnia implementację do dokumentu pakietu (oznacza to, **CDocument**-pochodnych obiektów) jako załącznik i wysłać go jako poczty. Ten załącznik jest odpowiednikiem polecenia Zapisz plik, który zapisuje (serializuje) zawartość dokumentu do wiadomości e-mail. Ta implementacja wywołuje od klienta poczty e-mail na komputerze użytkownika, aby zapewnić możliwość adres poczty i dodać temat i tekst wiadomości do wiadomości e-mail użytkownika. Użytkownicy widzą ich aplikacji poczty znanego interfejsu użytkownika. Ta funkcja jest dostarczana przez dwa **CDocument** funkcji elementów członkowskich: `OnFileSendMail` i `OnUpdateFileSendMail`.  
  
 MAPI musi odczytać pliku do wysłania załącznika. Jeśli aplikacja przechowuje otwarte podczas jego plików danych `OnFileSendMail` wywołanie funkcji plik musi zostać otwarty w trybie udziału, w którym umożliwiają wielu procesom dostępu do tego pliku.  
  
> [!NOTE]
>  Zastępowanie wersji `OnFileSendMail` dla klasy `COleDocument` poprawnie uchwytów złożone dokumenty.  
  
#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Aby zaimplementować polecenie Wyślij pocztę z MFC  
  
1.  Dodaj element menu, którego identyfikator polecenia za pomocą Edytora menu Visual C++ **ID_FILE_SEND_MAIL**.  
  
     Ten identyfikator polecenia jest udostępniany przez platformę w AFXRES. H. Polecenia można dodać do dowolnego menu, ale zazwyczaj jest ona dodawana do **pliku** menu.  
  
2.  Ręcznie dodaj następującą wartość do mapy wiadomości w dokumencie:  
  
     [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]  
  
    > [!NOTE]
    >  Ta mapa komunikatów działa w przypadku dokumentu pochodzące z jednej **CDocument** lub **COleDocument** — prawidłową klasę podstawową w obu przypadkach go przejmuje nawet, jeśli jest mapowanie wiadomości w klasie pochodnej dokumentu.  
  
3.  Tworzenie aplikacji.  
  
 W przypadku obsługi poczty jest dostępny, MFC włącza elementu menu z `OnUpdateFileSendMail` , a następnie przetwarza polecenie z `OnFileSendMail`. Jeśli obsługa poczty nie jest dostępna, MFC automatycznie usuwa elementu menu, aby użytkownik nie będzie on widoczny.  
  
> [!TIP]
>  Zamiast ręcznie dodawać wpisy mapy wiadomości, jak opisano wcześniej, okno właściwości klasy służy do mapowania komunikatów na funkcje. Aby uzyskać więcej informacji, zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).  
  
 Aby uzyskać odpowiednie informacje, zobacz [MAPI](../mfc/mapi.md) omówienie.  
  
 Aby uzyskać więcej informacji na temat **CDocument** funkcji elementów członkowskich, które umożliwiają MAPI, zobacz:  
  
-   [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)  
  
-   [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)  
  
-   [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)  
  
## <a name="see-also"></a>Zobacz też  
 [MAPI](../mfc/mapi.md)

