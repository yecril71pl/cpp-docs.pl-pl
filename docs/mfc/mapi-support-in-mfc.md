---
title: Obsługa MAPI w MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
ms.openlocfilehash: 9b873ca1b3384adab6487fb3af9dc1401aaad12c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281645"
---
# <a name="mapi-support-in-mfc"></a>Obsługa MAPI w MFC

MFC dostarcza obsługę podzestaw programu Microsoft Application programu interfejsu MAPI (Messaging) w klasie `CDocument`. W szczególności `CDocument` ma funkcje Członkowskie, które określają, czy obsługa poczty jest obecny na komputerze użytkownika końcowego, a jeśli tak, Włącz polecenia Wyślij pocztę, którego identyfikator standardowe polecenia jest ID_FILE_SEND_MAIL. Funkcja obsługi MFC dla tego polecenia umożliwia użytkownikowi wysłać dokument pocztą e-mail.

> [!TIP]
>  Mimo że MFC nie hermetyzuje całego zestawu funkcji MAPI, nadal wywołaniem MAPI funkcji bezpośrednio, tak jak można wywołać funkcji Win32 API bezpośrednio z programów MFC.

Zapewnianie Wyślij pocztę polecenia w aplikacji jest bardzo proste. Biblioteka MFC zawiera implementację do dokumentu pakietu (czyli `CDocument`— pochodzi obiekt) jako załącznik oraz wysyłać je jako wiadomości e-mail. Ten załącznik jest odpowiednikiem polecenia Zapisz plik, który zapisuje (serializuje) zawartość dokumentu do wiadomości e-mail. Ta implementacja wywołuje od klienta poczty e-mail na komputerze użytkownika, aby dać użytkownikowi możliwość adres wiadomości e-mail i Dodaj temat i tekst wiadomości do wiadomości e-mail. Użytkownicy widzą w interfejsie użytkownika aplikacji ich dobrze znanych poczty. Ta funkcjonalność jest dostarczana przez dwa `CDocument` elementów członkowskich: `OnFileSendMail` i `OnUpdateFileSendMail`.

MAPI musi odczytać pliku do wysłania załącznika. Jeśli aplikacja zachowuje swój plik danych otwarty podczas `OnFileSendMail` wywołanie funkcji, plik musi być otwarty w trybie udziału, które umożliwiają wielu procesom dostępu do tego pliku.

> [!NOTE]
>  Przesłanianie wersję `OnFileSendMail` dla klasy `COleDocument` poprawnie obsługuje złożone dokumentów.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Aby zaimplementować polecenie Wyślij pocztę z MFC

1. Użyj Edytora menu Visual C++, aby dodać element menu, którego identyfikator polecenia jest ID_FILE_SEND_MAIL.

   Ten identyfikator polecenia są dostarczane przez platformę w AFXRES. H. Polecenia można dodać do dowolnego menu, ale zazwyczaj jest dodawany do **pliku** menu.

1. Ręcznie dodaj następujący element do mapy komunikatów w dokumencie:

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Ta mapa komunikatów działa w przypadku dokumentu pochodzące z poziomu `CDocument` lub `COleDocument` — pobierał poprawnej klasie bazowej, w obu przypadkach, nawet jeśli jest mapowanie wiadomości w klasie pochodnej dokumentu.

1. Tworzenie aplikacji.

Jeśli poczty pomoc techniczna jest dostępna, MFC umożliwia danego elementu menu przy użyciu `OnUpdateFileSendMail` i następnie przetwarza polecenia za pomocą `OnFileSendMail`. Jeśli obsługa poczty nie jest dostępna, MFC automatycznie usuwa danego elementu menu, dzięki czemu użytkownik nie będzie ją widział.

> [!TIP]
>  Zamiast ręcznego dodawania wpisy mapy komunikatów, jak opisano wcześniej, w oknie właściwości klasy służy również do mapowania komunikatów do funkcji. Aby uzyskać więcej informacji, zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).

Aby uzyskać powiązane informacje, zobacz [MAPI](../mfc/mapi.md) Przegląd.

Aby uzyskać więcej informacji na temat `CDocument` funkcji elementów członkowskich, które umożliwiają MAPI, zobacz:

- [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Zobacz także

[MAPI](../mfc/mapi.md)
