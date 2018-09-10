---
title: Ograniczenia dotyczące wartości symbolu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.restrictions.value
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], value restrictions
- restrictions, symbol values
ms.assetid: 32467ec3-690b-4cd0-a4d0-7d189a3296cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b174e46df7822ddf5ffbc747d0a7eb3cd71245e
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315408"
---
# <a name="symbol-value-restrictions"></a>Ograniczenia dotyczące wartości symbolu

Wartością symboliczną, może być liczbą całkowitą, wyrażone w normalny sposób do #define dyrektywy preprocesora. Poniżej przedstawiono kilka przykładów wartości symboli:

```
18
4001
0x0012
-3456
```

Wartości symboli dla zasobów (akceleratorów, mapy bitowe, kursorów, okna dialogowe, ikony, menu, tabele ciągów i informacje o wersji) muszą być liczbami dziesiętnymi z zakresu od 0 do 32 767 (ale nie może być szesnastkowym). Wartości symboli dla części zasobów, takich jak formanty okna dialogowego lub poszczególne ciągi w tabeli ciągów może być z zakresu od 0 do 65,534 lub od-32 768 do 32 767 znaków.

Symbole zasobów to 16-bitowych liczb. Można je wprowadzić jako podpisane lub niepodpisane, jednak są one używane wewnętrznie jako liczb całkowitych bez znaku. Dlatego wartości ujemne będzie można rzutować na ich odpowiednich wartości dodatniej.

Poniżej przedstawiono pewne ograniczenia wartości symboli:

- Środowisko projektowe programu Visual Studio i MFC na użytek niektóre liczba zakresów specjalnych celów. Wszystkie liczby z zestawem najbardziej znaczący bit (-32 768 -1 lub 32768 do 65,534, w zależności od logowania) są zarezerwowane przez MFC.

- Nie można zdefiniować wartości symboliczną za pomocą innych ciągów symboli. Na przykład następująca definicja symbol nie jest obsługiwana:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Nie można użyć makra preprocesora z argumentami, jako wartość definicje. Na przykład:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   nie jest prawidłowym wyrażeniem niezależnie od tego, co `ID` daje w wyniku w czasie kompilacji.

- Aplikacja może mieć istniejący plik zawierający symboli zdefiniowanych za pomocą wyrażeń. Aby uzyskać więcej informacji na temat sposobu dołączać symbole jako symbole tylko do odczytu, zobacz [przy użyciu udostępnionych (tylko do odczytu) lub symbole obliczane](../windows/including-shared-read-only-or-calculated-symbols.md).

Aby uzyskać więcej informacji na temat zakresów liczb, zobacz [TN023: standardowe zasoby MFC](../mfc/tn023-standard-mfc-resources.md).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Zmiana wartości numerycznej symbolu](../windows/changing-a-symbol-s-numeric-value.md)  
[Ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md)  
[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)