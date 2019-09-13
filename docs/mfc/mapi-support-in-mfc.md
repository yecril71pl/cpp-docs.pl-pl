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
ms.openlocfilehash: e46eaf2bd84d4cebd2215ab2752ce3bb8e1eb9b3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907679"
---
# <a name="mapi-support-in-mfc"></a>Obsługa MAPI w MFC

MFC udostępnia obsługę podzestawu interfejsu programu Microsoft Messaging Application Program (MAPI) w klasie `CDocument`. W związku z tym program mafunkcjeczłonkowskie,któreokreślają,czyobsługapocztyjestobecnanakomputerzeużytkownikakońcowego,ajeślitak,należywłączyćpolecenieWyślijpocztąe-mail,któregoidentyfikatorpoleceniastandardowegotoID_FILE_SEND_MAIL.`CDocument` Funkcja obsługi MFC dla tego polecenia umożliwia użytkownikowi Wysyłanie dokumentu pocztą elektroniczną.

> [!TIP]
>  Chociaż MFC nie hermetyzuje całego zestawu funkcji MAPI, można nadal wywoływać funkcje MAPI bezpośrednio, podobnie jak można wywoływać Win32 API funkcje bezpośrednio z programów MFC.

Udostępnianie polecenia Wyślij pocztę w aplikacji jest bardzo proste. MFC udostępnia implementację dokumentu ( `CDocument`czyli obiekt pochodny) jako załącznik i wyślij ją jako wiadomość e-mail. Ten załącznik jest równoznaczny z poleceniem Zapisz plik, które zapisuje (serializować) zawartość dokumentu w wiadomości e-mail. Ta implementacja wywołuje klienta poczty na komputerze użytkownika w celu nadania użytkownikowi możliwości adresowania wiadomości e-mail i dodania tematu i tekstu wiadomości do wiadomości e-mail. Użytkownicy widzą interfejs użytkownika znanej aplikacji poczty. Ta funkcja jest dostarczana przez `CDocument` dwie funkcje składowe `OnUpdateFileSendMail`: `OnFileSendMail` i.

Interfejs MAPI musi odczytać plik w celu wysłania załącznika. Jeśli aplikacja utrzymuje plik danych otwarty podczas `OnFileSendMail` wywołania funkcji, należy otworzyć plik z trybem udostępniania, który umożliwia wielu procesom dostęp do pliku.

> [!NOTE]
>  Zastępowanie wersji `OnFileSendMail` dla klasy `COleDocument` prawidłowo obsługuje dokumenty złożone.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Aby zaimplementować polecenie wysyłania poczty z MFC

1. Użyj edytora menu C++ wizualizacji, aby dodać element menu, którego identyfikator polecenia to ID_FILE_SEND_MAIL.

   Ten identyfikator polecenia jest dostarczany przez strukturę w plik AFXRES. C. Polecenie można dodać do dowolnego menu, ale jest zazwyczaj dodawane do menu **plik** .

1. Dodaj ręcznie następujący element do mapy komunikatów dokumentu:

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Ta mapa komunikatów działa w przypadku dokumentu pochodzącego z `CDocument` albo `COleDocument` lub — pobiera w obu przypadkach poprawną klasę bazową, mimo że mapa wiadomości znajduje się w klasie dokumentu pochodnego.

1. Kompiluj aplikację.

Jeśli obsługa poczty jest dostępna, MFC włącza element menu za pomocą `OnUpdateFileSendMail` polecenia, a następnie przetwarza je `OnFileSendMail`w programie. Jeśli obsługa poczty jest niedostępna, MFC automatycznie usuwa element menu, dzięki czemu użytkownik nie zobaczy tego elementu.

> [!TIP]
>  Zamiast ręcznego dodawania wpisów mapy komunikatów, jak opisano wcześniej, można użyć [kreatora klas](reference/mfc-class-wizard.md) klas do mapowania komunikatów do funkcji. Aby uzyskać więcej informacji, zobacz [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).

Aby uzyskać powiązane informacje, zobacz Omówienie [MAPI](../mfc/mapi.md) .

Aby uzyskać więcej informacji na `CDocument` temat funkcji Członkowskich, które umożliwiają korzystanie z MAPI, zobacz:

- [CDocument:: OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument:: OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Zobacz także

[MAPI](../mfc/mapi.md)
