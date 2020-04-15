---
title: 'Kontrolki ActiveX MFC: implementacja właściwości zaawansowanych'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: d4f1265e6540e9f84bdb680e7948a4e308d31bb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364648"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>Kontrolki ActiveX MFC: implementacja właściwości zaawansowanych

W tym artykule opisano tematy związane z implementowanie właściwości zaawansowanych w formancie ActiveX.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

- [Właściwości tylko do odczytu i tylko do zapisu](#_core_read2donly_and_write2donly_properties)

- [Zwracanie kodów błędów z właściwości](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a>Właściwości tylko do odczytu i tylko do zapisu

Kreator dodawania właściwości zapewnia szybką i łatwą metodę implementowania właściwości tylko do odczytu lub tylko do zapisu dla formantu.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>Aby zaimplementować właściwość tylko do odczytu lub tylko do zapisu

1. Załaduj projekt formantu.

1. W widoku klasy rozwiń węzeł biblioteki formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj właściwość**.

   Spowoduje to otwarcie [Kreatora dodawania właściwości](../ide/names-add-property-wizard.md).

1. W polu **Nazwa właściwości** wpisz nazwę właściwości.

1. W przypadku **typu implementacji**kliknij pozycję **Pobierz/Ustaw metody**.

1. W polu **Typ właściwości** wybierz odpowiedni typ właściwości.

1. Jeśli chcesz właściwość tylko do odczytu, wyczyść nazwę funkcji Ustaw. Jeśli chcesz właściwość tylko do zapisu, wyczyść nazwę funkcji Pobierz.

1. Kliknij przycisk **Zakończ**.

Po wykonaniu tej czynności Kreator dodawania `SetNotSupported` właściwości `GetNotSupported` wstawia funkcję lub wpis mapy wysyłki zamiast normalnej funkcji Set lub Get.

Jeśli chcesz zmienić istniejącą właściwość jako tylko do odczytu lub tylko do zapisu, możesz ręcznie edytować mapę wysyłki i usunąć niepotrzebną funkcję Set lub Get z klasy kontrolnej.

Jeśli chcesz, aby właściwość była warunkowo tylko do odczytu lub tylko do zapisu (na przykład tylko wtedy, gdy formant `SetNotSupported` działa `GetNotSupported` w określonym trybie), można podać Set or Get funkcji, jak zwykle i wywołać lub funkcji, w stosownych przypadkach. Przykład:

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

Ten przykładowy `SetNotSupported` kod `m_bReadOnlyMode` wywołuje, jeśli element członkowski danych ma **wartość PRAWDA**. Jeśli **FALSE**, a następnie właściwość jest ustawiona na nową wartość.

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a>Zwracanie kodów błędów z właściwości

Aby wskazać, że wystąpił błąd podczas próby uzyskania lub `COleControl::ThrowError` ustawić właściwość, należy użyć funkcji, która przyjmuje SCODE (kod stanu) jako parametr. Można użyć wstępnie zdefiniowanego kodu SCODE lub zdefiniować jeden z własnych. Aby uzyskać listę wstępnie zdefiniowanych scodees i instrukcje dotyczące definiowania niestandardowych SCODEs, zobacz [Obsługi błędów w Formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w artykule ActiveX kontroli: Tematy zaawansowane.

Funkcje pomocnika istnieją dla najpopularniejszych wstępnie zdefiniowanych SCODE, takich jak [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported)i [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
> `ThrowError`jest przeznaczony do użycia tylko jako środek zwracania błędu z wewnątrz właściwości Get lub Set funkcji lub metody automatyzacji. Są to tylko razy, że odpowiedni program obsługi wyjątków będzie obecny na stosie.

Aby uzyskać więcej informacji na temat raportowania wyjątków w innych obszarach kodu, zobacz [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) i sekcji [Obsługi błędów w formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w artykule ActiveX Controls: Advanced Topics.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: właściwości](../mfc/mfc-activex-controls-properties.md)<br/>
[Kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](../mfc/reference/colecontrol-class.md)
