---
title: 'Kontrolki ActiveX MFC: Zaawansowana implementacja właściwości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4aa1116384ac9fd5212046f9a0b3354a3aa70d88
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416087"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>Kontrolki ActiveX MFC: implementacja właściwości zaawansowanych

W tym artykule opisano tematy związane z implementacją zaawansowane właściwości formantu ActiveX.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które wypierają ActiveX zobacz [formantów ActiveX](activex-controls.md).

- [Właściwości tylko do odczytu i tylko do zapisu](#_core_read2donly_and_write2donly_properties)

- [Zwracanie kodów błędów z właściwością](#_core_returning_error_codes_from_a_property)

##  <a name="_core_read2donly_and_write2donly_properties"></a> Właściwości tylko do odczytu i tylko do zapisu

Kreator dodawania właściwości zapewnia szybki i łatwy sposób zaimplementować właściwości tylko do odczytu lub tylko do zapisu dla formantu.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>Aby zaimplementować właściwości tylko do odczytu lub tylko do zapisu

1. Załaduj projekt formantu.

1. W widoku klas rozwiń węzeł biblioteki kontrolki.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj właściwość**.

     Spowoduje to otwarcie [Kreator dodawania właściwości](../ide/names-add-property-wizard.md).

1. W **nazwa właściwości** wpisz nazwę właściwości.

1. Aby uzyskać **typ implementacji**, kliknij przycisk **metod Get/Set**.

1. W **typ właściwości** wybierz odpowiedniego typu właściwości.

1. Jeśli chcesz, aby właściwość tylko do odczytu, wyczyść nazwą zestawu funkcji. Jeśli chcesz, aby właściwość tylko do zapisu, wyczyść nazwę funkcji Get.

9. Kliknij przycisk **Zakończ**.

Gdy to zrobisz, Kreator dodawania właściwości Wstawia funkcję `SetNotSupported` lub `GetNotSupported` we wpisie mapy wysyłania zamiast normalnego ustawić lub pobrać funkcji.

Jeśli chcesz zmienić istniejącą właściwość jako tylko do odczytu lub tylko do zapisu, można ręcznie edytować Mapa wysyłania i usunąć niepotrzebne funkcji Set lub Get z klasy formantu.

Jeśli chcesz, aby właściwość, która ma być warunkowo tylko do odczytu lub tylko do zapisu (na przykład tylko wtedy, gdy formant działa w określonym trybie), można zapewniają taką funkcję Set lub Get, jak normalne i wywoływać `SetNotSupported` lub `GetNotSupported` funkcji, gdzie jest to odpowiednie. Na przykład:

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

Ten przykładowy kod wywołuje `SetNotSupported` Jeśli `m_bReadOnlyMode` element członkowski danych jest **TRUE**. Jeśli **FALSE**, a następnie dla właściwości ustawiono nową wartość.

##  <a name="_core_returning_error_codes_from_a_property"></a> Zwracanie kodów błędów z właściwością

Aby wskazać, że wystąpił błąd podczas próby pobrania lub ustawienia właściwości, należy użyć `COleControl::ThrowError` funkcji, która przyjmuje SCODE (kod stanu), jako parametr. Można użyć wstępnie zdefiniowanych SCODE lub zdefiniować własny. Aby uzyskać listę wstępnie zdefiniowanych SCODEs i instrukcje dotyczące definiowania SCODEs niestandardowych, zobacz [obsługi błędów w tym formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w kontrolkach ActiveX artykułu: Tematy zaawansowane.

Funkcje pomocnicze istnieje dla najbardziej typowych predefiniowanymi SCODEs, takimi jak [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), i [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
>  `ThrowError` jest przeznaczona do użycia wyłącznie jako środek zwróci błąd z w ramach właściwości Get lub Set funkcja lub metoda automatyzacji. Są to tylko razy, które będą znajdować się program obsługi wyjątków odpowiednie znajduje się na stosie.

Aby uzyskać więcej informacji na temat raportowania wyjątków w innych obszarach kodu, zobacz [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) oraz sekcję [obsługi błędów w tym formancie ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) w artykule kontrolek ActiveX: Zaawansowane Tematy.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Kontrolki ActiveX MFC: właściwości](../mfc/mfc-activex-controls-properties.md)<br/>
[Kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md)<br/>
[Klasa COleControl](../mfc/reference/colecontrol-class.md)
