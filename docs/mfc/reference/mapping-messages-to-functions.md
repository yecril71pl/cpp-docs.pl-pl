---
title: Mapowanie komunikatów na funkcje
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.mapping.msg.function
helpviewer_keywords:
- Windows messages [MFC], adding message handlers
- message maps [MFC], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
ms.openlocfilehash: 33aa12626e92eb40606e3ec9b12ebb7bcac571ec
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66741657"
---
# <a name="mapping-messages-to-functions"></a>Mapowanie komunikatów na funkcje

W oknie właściwości pozwala powiązać programy obsługi komunikatów (funkcje elementów członkowskich klasy interfejsu użytkownika MFC) na komunikaty generowane przez zasoby aplikacji. Używają [mapy wiadomości MFC](../../mfc/messages-and-commands-in-the-framework.md) Aby utworzyć powiązanie.

Podczas tworzenia nowej klasy pochodzącej od jednej z klas framework za pomocą widoku klasy, jego automatycznie umieszcza kompletne i funkcjonalne klasy nagłówka (.h) i implementacji (.cpp) plików, które określisz.

> [!NOTE]
>  Aby dodać nową klasę, która nie obsługuje wiadomości, należy utworzyć klasę bezpośrednio w edytorze tekstów.

### <a name="to-define-or-remove-a-message-handler-using-the-properties-window"></a>Aby zdefiniować lub usuń program obsługi komunikatów za pomocą okna właściwości

1. W widoku klas kliknij klasy.

1. W oknie dialogowym właściwości kliknij **wiadomości** przycisku.

    > [!NOTE]
    >  **Wiadomości** przycisk jest dostępny po wybraniu nazwy klasy w widoku klas lub po kliknięciu w oknie źródła.

   Jeżeli projekt zawiera program obsługi wiadomości, nazwę programu obsługi, który pojawia się w prawej kolumnie obok komunikatu.

1. Jeśli żadna procedura obsługi wiadomości, kliknij komórkę w prawej kolumnie w oknie dialogowym właściwości, aby wyświetlić sugerowane nazwę procedury obsługi jako \<Dodaj >*HandlerName*. (Na przykład, program obsługi komunikatów WM_TIMER sugeruje \<Dodaj >`OnTimer`).

1. Kliknij nazwę sugerowaną można dodać kodu klasy zastępczej dla funkcji.

1. Edytowanie programu obsługi komunikatów, kliknij dwukrotnie komunikat w widoku klas i edytowanie kodu w oknie źródła.

Aby usunąć program obsługi komunikatów, kliknij dwukrotnie program obsługi w prawej kolumnie, a następnie wybierz \<Usuń >*HandlerName*. Kod funkcji jest opatrzona komentarzem.

## <a name="see-also"></a>Zobacz także

[Handler komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnych](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Dodawanie obsługi zdarzeń dla kontrolek okna dialogowego](../../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Nawigacja w strukturze klas](../../ide/navigate-code-cpp.md)
