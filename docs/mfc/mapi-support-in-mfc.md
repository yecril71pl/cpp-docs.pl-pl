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
ms.openlocfilehash: 3024f744407cf33c8dfad8a6f7af736e0f8061ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356998"
---
# <a name="mapi-support-in-mfc"></a>Obsługa MAPI w MFC

MFC zapewnia obsługę podzbioru interfejsu programu aplikacji programu usługi `CDocument`Microsoft Messaging (MAPI) w klasie . W szczególności `CDocument` ma funkcje członkowskie, które określają, czy obsługa poczty jest obecny na komputerze użytkownika końcowego, a jeśli tak, włączyć polecenie Wyślij pocztę, którego standardowy identyfikator polecenia jest ID_FILE_SEND_MAIL. Funkcja obsługi MFC dla tego polecenia umożliwia użytkownikowi wysyłanie dokumentu za pośrednictwem poczty elektronicznej.

> [!TIP]
> Chociaż MFC nie hermetyzuje cały zestaw funkcji MAPI, nadal można wywołać funkcje MAPI bezpośrednio, podobnie jak można wywołać funkcje interfejsu API Win32 bezpośrednio z programów MFC.

Podanie polecenia Wyślij pocztę w aplikacji jest bardzo proste. MFC udostępnia implementacji do pakietu dokumentu `CDocument`(czyli -derived obiektu) jako załącznik i wysłać go jako mail. Ten załącznik jest odpowiednikiem polecenia Zapisywanie pliku, które zapisuje (serializuje) zawartość dokumentu do wiadomości e-mail. Ta implementacja wzywa klienta poczty na komputerze użytkownika, aby dać użytkownikowi możliwość adres mail i dodać temat i tekst wiadomości do wiadomości e-mail. Użytkownicy widzą interfejs użytkownika swojej znanej aplikacji poczty. Ta funkcja jest dostarczana przez dwie `CDocument` funkcje członkowskie: `OnFileSendMail` i `OnUpdateFileSendMail`.

MAPI musi odczytać plik, aby wysłać załącznik. Jeśli aplikacja zachowuje swój plik `OnFileSendMail` danych otwarty podczas wywołania funkcji, plik musi zostać otwarty w trybie udostępniania, który umożliwia dostęp do pliku wielu procesom.

> [!NOTE]
> Nadrzędna wersja `OnFileSendMail` dla klasy `COleDocument` poprawnie obsługuje dokumenty złożone.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Aby zaimplementować polecenie Wyślij pocztę z MFC

1. Użyj edytora menu Visual C++, aby dodać element menu, którego identyfikator polecenia jest ID_FILE_SEND_MAIL.

   Ten identyfikator polecenia jest dostarczany przez platformę w AFXRES. H. Polecenie można dodać do dowolnego menu, ale zwykle jest ono dodawane do menu **Plik.**

1. Ręcznie dodaj następujące elementy do mapy wiadomości dokumentu:

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Ta mapa wiadomości działa dla dokumentu `CDocument` pochodzącego z jednej lub `COleDocument` — pobiera poprawną klasę podstawową w obu przypadkach, nawet jeśli mapa wiadomości znajduje się w klasie dokumentu pochodnego.

1. Tworzenie aplikacji.

Jeśli obsługa poczty jest dostępna, MFC `OnUpdateFileSendMail` włącza element menu, `OnFileSendMail`a następnie przetwarza polecenie za pomocą . Jeśli obsługa poczty nie jest dostępna, MFC automatycznie usuwa element menu, więc użytkownik nie będzie go widzieć.

> [!TIP]
> Zamiast ręcznie dodawać wpisy mapy wiadomości, jak opisano wcześniej, można użyć [Kreatora klas](reference/mfc-class-wizard.md) do mapowania wiadomości do funkcji. Aby uzyskać więcej informacji, zobacz [Mapowanie wiadomości do funkcji](../mfc/reference/mapping-messages-to-functions.md).

Aby uzyskać powiązane informacje, zobacz omówienie [MAPI.](../mfc/mapi.md)

Aby uzyskać więcej `CDocument` informacji na temat funkcji członkowskich, które włączą mapi, zobacz:

- [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Zobacz też

[MAPI](../mfc/mapi.md)
