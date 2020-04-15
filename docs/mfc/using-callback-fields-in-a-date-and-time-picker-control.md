---
title: Używanie pól wywołania zwrotnego w formancie selektora dat i godzin
ms.date: 11/04/2016
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
ms.openlocfilehash: 50350e51b6747d8c010db9d0dcaa9dff2e56e1f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366554"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Używanie pól wywołania zwrotnego w formancie selektora dat i godzin

Oprócz znaków formatu standardowego definiujących pola selektora daty i godziny można dostosować dane wyjściowe, określając niektóre części niestandardowego ciągu formatu jako pola wywołania zwrotnego. Aby zadeklarować pole wywołania zwrotnego, należy dołączyć jeden lub więcej znaków "X" (kod ASCII 88) w dowolnym miejscu w treści ciągu formatu. Na przykład następujący ciąg "Today is: 'yy'/'MM'/'dd' (Day 'X')'"powoduje, że formant selektora daty i godziny wyświetla bieżącą wartość jako rok, po którym następuje miesiąc, data i wreszcie dzień roku.

> [!NOTE]
> Liczba X w polu wywołania zwrotnego nie odpowiada liczbie znaków, które będą wyświetlane.

Można odróżnić wiele pól wywołania zwrotnego w ciągu niestandardowym, powtarzając znak "X". Tak więc ciąg formatu "XXdddmmMdd", "yyyXXX" zawiera dwa unikatowe pola wywołania zwrotnego, "XX" i "XXX".

> [!NOTE]
> Pola wywołania zwrotnego są traktowane jako prawidłowe pola, więc aplikacja musi być przygotowana do obsługi komunikatów powiadomień DTN_WMKEYDOWN.

Implementowanie pól wywołania zwrotnego w formancie selektora daty i godziny składa się z trzech części:

- Inicjowanie ciągu formatu niestandardowego

- Obsługa powiadomienia o DTN_FORMATQUERY

- Obsługa powiadomienia o DTN_FORMAT

## <a name="initializing-the-custom-format-string"></a>Inicjowanie ciągu formatu niestandardowego

Inicjowanie niestandardowego ciągu `CDateTimeCtrl::SetFormat`za pomocą wywołania . Aby uzyskać więcej informacji, zobacz [Używanie ciągów formatu niestandardowego w formancie selektora daty i godziny](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Wspólne miejsce, aby ustawić ciąg formatu niestandardowego jest `OnInitDialog` w `OnInitialUpdate` funkcji zawierającej klasy okna dialogowego lub funkcji klasy widoku zawierającego.

## <a name="handling-the-dtn_formatquery-notification"></a>Obsługa powiadomienia o DTN_FORMATQUERY

Gdy formant analizuje ciąg formatu i napotka pole wywołania zwrotnego, aplikacja wysyła DTN_FORMAT i DTN_FORMATQUERY komunikatów powiadomień. Ciąg pola wywołania zwrotnego jest dołączony do powiadomień, dzięki czemu można określić, które pole wywołania zwrotnego jest wyszukiwane.

Powiadomienie DTN_FORMATQUERY jest wysyłane w celu pobrania maksymalnego dopuszczalnego rozmiaru w pikselach ciągu, który będzie wyświetlany w bieżącym polu wywołania zwrotnego.

Aby poprawnie obliczyć tę wartość, należy obliczyć wysokość i szerokość ciągu, który ma zostać zastąpiony przez pole, przy użyciu czcionki wyświetlanej formantu. Rzeczywiste obliczenie ciągu można łatwo osiągnąć za pomocą wywołania funkcji [GetTextExtentPoint32](/windows/win32/api/wingdi/nf-wingdi-gettextextentpoint32w) Win32. Po określeniu rozmiaru przekazać wartość z powrotem do aplikacji i zakończyć funkcję obsługi.

Poniższy przykład jest jedną z metod dostarczania rozmiaru ciągu wywołania zwrotnego:

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

Po obliczeniu rozmiaru bieżącego pola wywołania zwrotnego należy podać wartość tego pola. Odbywa się to w programie obsługi dla powiadomienia DTN_FORMAT.

## <a name="handling-the-dtn_format-notification"></a>Obsługa powiadomienia DTN_FORMAT

Powiadomienie DTN_FORMAT jest używane przez aplikację do żądania ciągu znaków, który zostanie podstawiony. Poniższy przykład pokazuje jedną możliwą metodę:

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
> Wskaźnik do **NMDATETIMEFORMAT** struktury znajduje się przez rzutowanie pierwszy parametr programu obsługi powiadomień do odpowiedniego typu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
