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
ms.openlocfilehash: 874f73df3dda3a720d4346ae3fb0136c662221db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403584"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Używanie pól wywołania zwrotnego w formancie selektora dat i godzin

Oprócz standardowych znaków formatu, które definiują pola selektora daty i godziny dane wyjściowe można dostosować, określając niektórych części ciągu formatu niestandardowego pola wywołania zwrotnego. Aby zadeklarować pole wywołania zwrotnego, obejmują co najmniej jeden znak "X" (ASCII kod 88) dowolnym miejscu w treści ciągu formatu. Na przykład, następujący ciąg "" dziś jest: "yy" / "MM" / "dd" (dzień "X") ""powoduje, że kontrolka selektora daty i godziny wyświetlić bieżące wartości jako roku, miesiąca, daty, a na koniec dnia roku.

> [!NOTE]
>  Liczba znakiem x w wywołaniu zwrotnym pola nie odpowiada żadnemu liczbę znaków, które będą wyświetlane.

Można rozróżnić wielu pól wywołania zwrotnego w niestandardowy ciąg, powtarzając znak "X". W związku z tym, ciąg formatu "XXddddMMMdd", "yyyXXX" zawiera dwa pola unikatowe wywołanie zwrotne "XX" i "XXX".

> [!NOTE]
>  Pola wywołania zwrotnego są traktowane jako prawidłowych pól, dzięki czemu Twoja aplikacja musi być przygotowana do obsługi komunikatów powiadomień dotyczących DTN_WMKEYDOWN.

Implementowanie pól wywołania zwrotnego w kontrolce selektora daty i godziny składa się z trzech części:

- Inicjowanie ciągu formatu niestandardowego

- Obsługa dtn_formatquery — powiadomienie

- Obsługa dtn_format — powiadomienie

## <a name="initializing-the-custom-format-string"></a>Inicjowanie ciągu formatu niestandardowego

Niestandardowy ciąg przy użyciu wywołania do zainicjowania `CDateTimeCtrl::SetFormat`. Aby uzyskać więcej informacji, zobacz [przy użyciu niestandardowe ciągi formatów daty i czasu kontrolkę selektora](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Typowe miejsca ustawienia ciągu formatu niestandardowego jest `OnInitDialog` funkcja zawierającego klasy okien dialogowych lub `OnInitialUpdate` funkcji zawierającego klasy widoku.

## <a name="handling-the-dtnformatquery-notification"></a>Obsługa dtn_formatquery — powiadomienie

Gdy formant analizuje ciąg formatu i napotka pola wywołania zwrotnego, aplikacja wysyła DTN_FORMAT i dtn_formatquery — powiadomienie. Ciąg pola wywołania zwrotnego jest dołączony do powiadomienia, dzięki czemu można określić pole wywołanie zwrotne, które są odpytywane.

Dtn_formatquery — powiadomienie jest wysyłane do pobierania maksymalny dozwolony rozmiar w pikselach ciąg, który pojawi się w bieżącej wartości pola wywołania zwrotnego.

Aby poprawnie obliczyć tej wartości, musisz obliczyć wysokości i szerokości ciągu do zastąpienia dla pola, przy użyciu czcionki wyświetlania kontrolki. Rzeczywiste obliczenia w ciągu to z łatwością przeprowadzić przy użyciu wywołania do [GetTextExtentPoint32](/windows/desktop/api/wingdi/nf-wingdi-gettextextentpoint32a) funkcję Win32. Po określeniu rozmiar przekazać wartość do aplikacji i zakończyć działanie funkcji obsługi.

Poniższy przykład przedstawia jedną metodę podawania rozmiar ciągu wywołania zwrotnego:

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

Po został obliczony rozmiar bieżącego pola wywołania zwrotnego, należy podać wartość dla pola. Jest to realizowane w Obsługa dtn_format — powiadomienie.

## <a name="handling-the-dtnformat-notification"></a>Obsługa dtn_format — powiadomienie

Dtn_format — powiadomienie jest używany przez aplikację do żądania ciąg znaków, który zostanie zastąpiony. Poniższy przykład przedstawia jedną z możliwych metod:

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
>  Wskaźnik do **NMDATETIMEFORMAT** struktury znajduje się przez rzutowanie pierwszy parametr obsługi powiadomień do odpowiedniego typu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
