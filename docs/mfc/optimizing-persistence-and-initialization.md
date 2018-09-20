---
title: Optymalizacja stanu trwałego i inicjalizacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 395fc71f42dd947de331051233a5dcce086f7bb3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400812"
---
# <a name="optimizing-persistence-and-initialization"></a>Optymalizacja stanu trwałego i inicjalizacji

Domyślnie stanu trwałego i inicjalizacji w kontrolce są obsługiwane przez `DoPropExchange` funkcja elementu członkowskiego. W kontrolce typowe tej funkcji zawiera kilka wywołań **PX_** funkcji (`PX_Color`, `PX_Font`i tak dalej), jeden dla każdej właściwości.

Takie podejście ma tę zaletę, że jeden `DoPropExchange` implementacji może służyć do inicjowania, trwałości w formacie binarnym i trwałości w formacie tak zwane "-zbioru właściwości" używana przez niektóre kontenery. Ta funkcja jeden udostępnia wszystkie informacje o właściwościach i ich wartości domyślne w jednym wygodnym miejscu.

Jednak ta ogólności pochodzi kosztem wydajności. **PX_** funkcje Pobierz ich elastyczność za pośrednictwem wielowarstwowego implementacji, które są natury mniej wydajne niż bardziej bezpośrednie, ale mniej elastyczne podejście. Ponadto jeśli kontrola przechodzi do wartości domyślnej **PX_** działać, musi być podana zawsze, nawet w sytuacjach, gdy wartość domyślna nie musi być używana wartość domyślna. Jeśli Generowanie wartością domyślną jest proste zadanie (na przykład, gdy wartości są uzyskiwane z właściwością otoczenia), a następnie dodatkowy, niepotrzebne zadania są wykonywane w przypadkach, gdy nie jest używana wartość domyślna.

Możesz poprawić wydajność trwałości binarnych kontroli nad przez zastąpienie kontroli nad `Serialize` funkcji. Domyślna implementacja tej funkcji elementu członkowskiego nawiązuje połączenie z `DoPropExchange` funkcji. Przez zastąpienie go, możesz zapewnić bardziej bezpośrednie implementacji dla binarnego trwałości. Na przykład, rozważmy ten `DoPropExchange` funkcji:

[!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

Aby zwiększyć wydajność, trwałość binarne tej kontrolki, można zastąpić `Serialize` funkcji w następujący sposób:

[!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

`dwVersion` Zmienna lokalna może służyć do wykrywania wersji trwały stan formantu jest załadowany lub zapisać. Można użyć tej zmiennej, zamiast wywoływać metodę [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion).

Aby zapisać małej ilości miejsca w trwałym formacie dla **BOOL** właściwości (i być zgodny z formatem produkowane przez `PX_Bool`), można przechowywać właściwość jako **BAJTÓW**, wykonując następujące czynności:

[!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

Należy pamiętać, że w przypadku obciążenia jest używana zmienna tymczasowa, a następnie jego wartość jest przypisywana, zamiast rzutowanie *m_boolProp* do **BAJTÓW** odwołania. Technika rzutowania spowoduje tylko jeden bajt *m_boolProp* jest modyfikowany, pozostawiając pozostałe bajty niezainicjowana.

Dla tej samej kontrolki inicjowanie kontrolki można zoptymalizować poprzez zastąpienie [COleControl::OnResetState](../mfc/reference/colecontrol-class.md#onresetstate) w następujący sposób:

[!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

Mimo że `Serialize` i `OnResetState` zostały nadpisane, `DoPropExchange` funkcji powinny być przechowywane bez zmian, ponieważ jest nadal używana potrzeby stanu trwałego w formacie zbioru właściwości. Jest to ważne, aby zachować wszystkie trzy te funkcje, aby upewnić się, formant spójnie zarządza jej właściwości niezależnie od tego, w którym trwałość używa mechanizmu kontenera.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC: optymalizacja](../mfc/mfc-activex-controls-optimization.md)

