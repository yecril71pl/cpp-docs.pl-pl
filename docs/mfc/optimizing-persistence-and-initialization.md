---
title: Optymalizacja stanu trwałego i inicjalizacji
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
ms.openlocfilehash: 57b98f7e2e4f9e23175b8b01c2e37ff49c499949
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623998"
---
# <a name="optimizing-persistence-and-initialization"></a>Optymalizacja stanu trwałego i inicjalizacji

Domyślnie trwałość i Inicjalizacja w formancie są obsługiwane przez `DoPropExchange` funkcję członkowską. W przypadku typowej kontrolki ta funkcja zawiera wywołania kilku funkcji **PX_** ( `PX_Color` , `PX_Font` , i tak dalej), po jednej dla każdej właściwości.

Ta metoda ma zaletę, że `DoPropExchange` można użyć pojedynczej implementacji do inicjowania, trwałości w formacie binarnym oraz trwałości w formacie "właściwości-Work" używanym przez niektóre kontenery. Ta funkcja udostępnia wszystkie informacje o właściwościach i ich wartości domyślne w jednym wygodnym miejscu.

Ta ogólna wartość ma jednak miejsce w kosztach wydajności. **PX_** funkcje zapewniają elastyczność dzięki wielowarstwowym implementacjom, które są z nieodłączną wydajnością mniej wydajną, ale mniej elastycznym podejściem. Ponadto, Jeśli kontrolka przekazuje wartość domyślną do funkcji **PX_** , ta wartość domyślna musi być dostarczana za każdym razem, nawet w sytuacjach, gdy wartość domyślna nie może być używana. Jeśli wartość domyślna to zadanie nieproste (na przykład gdy wartość jest pobierana z właściwości otoczenia), to dodatkowe, niepotrzebne działania są wykonywane w przypadkach, gdy wartość domyślna nie jest używana.

Można poprawić wydajność danych binarnych formantu, zastępując funkcję kontrolki `Serialize` . Domyślna implementacja tej funkcji składowej wywołuje wywołanie `DoPropExchange` funkcji. Zastępując go, można zapewnić bardziej bezpośrednią implementację dla trwałości binarnej. Rozważmy na przykład tę `DoPropExchange` funkcję:

[!code-cpp[NVC_MFC_AxOpt#1](codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

Aby zwiększyć wydajność danych binarnych tej kontrolki, można przesłonić tę `Serialize` funkcję w następujący sposób:

[!code-cpp[NVC_MFC_AxOpt#2](codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

`dwVersion`Zmienna lokalna może służyć do wykrywania wersji trwałego lub zapisywanych Stanów trwałych kontrolek. Tej zmiennej można użyć zamiast wywołania [CPropExchange:: GetVersion](reference/cpropexchange-class.md#getversion).

Aby zaoszczędzić małe miejsce w trwałym formacie dla właściwości **bool** (i zachować zgodność z formatem utworzonym przez `PX_Bool` ), można przechowywać właściwość jako **bajt**w następujący sposób:

[!code-cpp[NVC_MFC_AxOpt#3](codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

Należy zauważyć, że w przypadku ładowania jest używana zmienna tymczasowa, a następnie zostanie przypisana wartość, a nie rzutowanie *m_boolProp* na odwołanie do **bajtu** . Metoda rzutowania spowodowałaby modyfikację tylko jednego bajtu *m_boolProp* , pozostawiając pozostałe bajty niezainicjowane.

Dla tej samej kontrolki można zoptymalizować inicjalizację kontrolki, zastępując [COleControl:: OnResetState](reference/colecontrol-class.md#onresetstate) w następujący sposób:

[!code-cpp[NVC_MFC_AxOpt#4](codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

Chociaż `Serialize` i `OnResetState` zostały zastąpione, `DoPropExchange` funkcja powinna być nienaruszona, ponieważ jest nadal używana do trwałości w formacie zbioru właściwości. Ważne jest, aby zachować wszystkie trzy z tych funkcji, aby upewnić się, że formant zarządza swoimi właściwościami, niezależnie od tego, który mechanizm trwałości jest używany przez kontener.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC: optymalizacja](mfc-activex-controls-optimization.md)
