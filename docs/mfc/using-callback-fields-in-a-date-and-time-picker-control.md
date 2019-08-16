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
ms.openlocfilehash: 5d08c349253e62c15553cfa0452cee930b1a1876
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513504"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Używanie pól wywołania zwrotnego w formancie selektora dat i godzin

Oprócz znaków standardowego formatu, które definiują pola selektora daty i godziny, można dostosować dane wyjściowe, określając niektóre części niestandardowego ciągu formatu jako pola wywołania zwrotnego. Aby zadeklarować pole wywołania zwrotnego, należy dołączyć jeden lub więcej znaków "X" (kod ASCII 88) w dowolnym miejscu w treści ciągu formatu. Na przykład następujący ciąg "" dzisiaj to: "RR"/"MM"/"DD" (dzień "X") "" powoduje, że kontrolka selektora daty i godziny wyświetla bieżącą wartość jako rok, a następnie miesiąc, datę i dzień roku.

> [!NOTE]
>  Liczba znaków w polu wywołania zwrotnego jest niezgodna z liczbą wyświetlanych wartości.

Można rozróżnić wiele pól wywołania zwrotnego w niestandardowym ciągu przez powtarzanie znaku "X". W ten sposób ciąg formatu "XXddddMMMdd", "yyyXXX" zawiera dwa unikatowe pola wywołania zwrotnego, "XX" i "XXX".

> [!NOTE]
>  Pola wywołania zwrotnego są traktowane jako prawidłowe pola, więc aplikacja musi być przygotowana do obsługi komunikatów powiadomień DTN_WMKEYDOWN.

Implementowanie pól wywołania zwrotnego w kontrolce selektora daty i godziny składa się z trzech części:

- Inicjowanie ciągu formatu niestandardowego

- Obsługa powiadomienia DTN_FORMATQUERY

- Obsługa powiadomienia DTN_FORMAT

## <a name="initializing-the-custom-format-string"></a>Inicjowanie ciągu formatu niestandardowego

Zainicjuj ciąg niestandardowy wywołaniem metody `CDateTimeCtrl::SetFormat`. Aby uzyskać więcej informacji, zobacz [Używanie niestandardowych ciągów formatu w kontrolce selektora dat i godzin](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Typowym miejscem, w którym można ustawić ciąg formatu niestandardowego, `OnInitDialog` jest funkcja klasy dialogowej lub `OnInitialUpdate` funkcji zawierającej klasy widoku.

## <a name="handling-the-dtn_formatquery-notification"></a>Obsługa powiadomienia DTN_FORMATQUERY

Gdy formant analizuje ciąg formatu i napotka pole wywołania zwrotnego, aplikacja wysyła komunikaty powiadomień DTN_FORMAT i DTN_FORMATQUERY. Ciąg pola wywołania zwrotnego jest dołączany do powiadomień, dzięki czemu można określić, które pole wywołania zwrotnego jest wysyłane.

Powiadomienie DTN_FORMATQUERY jest wysyłane w celu pobrania maksymalnego dozwolonego rozmiaru w pikselach ciągu, który będzie wyświetlany w polu bieżące wywołanie zwrotne.

Aby prawidłowo obliczyć tę wartość, należy obliczyć wysokość i szerokość ciągu, który ma zostać zastąpiony dla pola przy użyciu czcionki wyświetlania kontrolki. Rzeczywiste obliczenie ciągu jest łatwo osiągane za pomocą wywołania funkcji Win32 [GetTextExtentPoint32](/windows/win32/api/wingdi/nf-wingdi-gettextextentpoint32w) . Po ustaleniu rozmiaru przekaż wartość z powrotem do aplikacji i wyjdź z funkcji obsługi.

Poniższy przykład jest jedną metodą podawania rozmiaru ciągu wywołania zwrotnego:

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

Po obliczeniu rozmiaru bieżącego pola wywołania zwrotnego należy podać wartość dla tego pola. W tym celu należy wykonać procedurę obsługi dla powiadomienia DTN_FORMAT.

## <a name="handling-the-dtn_format-notification"></a>Obsługa powiadomienia DTN_FORMAT

Powiadomienie DTN_FORMAT jest używane przez aplikację do żądania ciągu znaków, który zostanie zastąpiony. Poniższy przykład ilustruje jedną z możliwych metod:

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
>  Wskaźnik do struktury **NMDATETIMEFORMAT** został znaleziony przez rzutowanie pierwszego parametru procedury obsługi powiadomień na właściwy typ.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
