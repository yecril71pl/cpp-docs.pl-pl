---
title: 'Kontrolki ActiveX MFC: implementacja właściwości zaawansowanych'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: f5abef4db2f9c6d375428c0b0fd313198ce6283f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621218"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>Kontrolki ActiveX MFC: implementacja właściwości zaawansowanych

W tym artykule opisano tematy związane z wdrażaniem zaawansowanych właściwości w kontrolce ActiveX.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

- [Właściwości tylko do odczytu i tylko do zapisu](#_core_read2donly_and_write2donly_properties)

- [Zwracanie kodów błędów z właściwości](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a>Właściwości tylko do odczytu i tylko do zapisu

Kreator dodawania właściwości zapewnia szybką i łatwą metodę zaimplementowania właściwości tylko do odczytu lub tylko do zapisu dla kontrolki.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>Aby zaimplementować właściwość tylko do odczytu lub tylko do zapisu

1. Załaduj projekt kontrolki.

1. W Widok klasy rozwiń węzeł Biblioteka formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.

   Spowoduje to otwarcie [Kreatora dodawania właściwości](../ide/names-add-property-wizard.md).

1. W polu **Nazwa właściwości** wpisz nazwę swojej właściwości.

1. W obszarze **Typ implementacji**kliknij pozycję **Pobierz/ustaw metody**.

1. W polu **Typ właściwości** wybierz odpowiedni typ dla właściwości.

1. Jeśli chcesz ustawić właściwość tylko do odczytu, usuń zaznaczenie pola wyboru Nazwa funkcji. Jeśli chcesz mieć właściwość tylko do zapisu, wyczyść pole wyboru Pobierz nazwę funkcji.

1. Kliknij przycisk **Zakończ**.

Gdy to zrobisz, Kreator dodawania właściwości Wstawia funkcję `SetNotSupported` lub `GetNotSupported` we wpisie mapy wysyłania zamiast normalnego zestawu lub funkcji get.

Jeśli chcesz zmienić istniejącą właściwość na wartość tylko do odczytu lub tylko do zapisu, możesz ręcznie edytować mapę wysyłkową i usunąć niezbędną funkcję Set lub Get z klasy Control.

Jeśli chcesz, aby właściwość była warunkowo tylko do odczytu lub tylko do zapisu (na przykład tylko wtedy, gdy formant działa w określonym trybie), możesz dostarczyć funkcję Set lub Get jako normalną i wywoływać `SetNotSupported` funkcję lub, `GetNotSupported` tam gdzie to konieczne. Przykład:

[!code-cpp[NVC_MFC_AxUI#29](codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

Ten przykładowy kod wywołuje `SetNotSupported` , jeśli `m_bReadOnlyMode` element członkowski danych ma **wartość true**. W przypadku **wartości false**właściwość jest ustawiana na nową wartość.

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a>Zwracanie kodów błędów z właściwości

Aby wskazać, że wystąpił błąd podczas próby pobrania lub ustawienia właściwości, należy użyć `COleControl::ThrowError` funkcji, która przyjmuje jako parametr SCODE (kod stanu). Możesz użyć wstępnie zdefiniowanego SCODE lub zdefiniować jeden z nich. Aby uzyskać listę wstępnie zdefiniowanych SCODEs i instrukcje definiowania niestandardowych SCODEs, zobacz temat [Obsługa błędów w kontrolce ActiveX](mfc-activex-controls-advanced-topics.md) w artykule formanty ActiveX: Tematy zaawansowane.

Istnieją funkcje pomocnika dla najpopularniejszych wstępnie zdefiniowanych SCODEs, takich jak [COleControl:: SetNotSupported](reference/colecontrol-class.md#setnotsupported), [COleControl:: GetNotSupported](reference/colecontrol-class.md#getnotsupported)i [COleControl:: SetNotPermitted](reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
> `ThrowError`ma być używany tylko jako środek zwrócenia błędu z funkcji get lub set właściwości lub metody automatyzacji. Są to jedyne sytuacje, w których na stosie będzie obecny odpowiedni program obsługi wyjątków.

Aby uzyskać więcej informacji na temat zgłaszania wyjątków w innych obszarach kodu, zobacz [COleControl:: FireError —](reference/colecontrol-class.md#fireerror) i sekcja [Obsługa błędów w kontrolce ActiveX](mfc-activex-controls-advanced-topics.md) w artykule formanty ActiveX: Tematy zaawansowane.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: właściwości](mfc-activex-controls-properties.md)<br/>
[Kontrolki ActiveX MFC: metody](mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](reference/colecontrol-class.md)
