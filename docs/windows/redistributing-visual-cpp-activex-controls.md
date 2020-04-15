---
title: Redystrybuowanie formantów ActiveX programu Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
ms.openlocfilehash: 4c7806502024789ed41f3043d7db6c87c7c71ee3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359879"
---
# <a name="redistributing-visual-c-activex-controls"></a>Redystrybuowanie formantów ActiveX programu Visual C++

Visual C++ 6.0 dostarcza formantów ActiveX, których można używać w aplikacjach, które następnie redystrybuujesz. Te formanty nie są już uwzględniane w języku Visual C++. Zgodnie z umowami licencyjnymi dla programu Visual C++ 6.0 można redystrybuować te formanty z aplikacjami opracowanymi w języku Visual C++.

> [!NOTE]
> Visual C++ 6.0 nie jest już obsługiwany przez firmę Microsoft.

Aby uzyskać listę redystrybucyjnych formantów Visual C++ 6.0 ActiveX, zobacz Common\Redist\Redist.txt na dysku 1 dysku CD produktu Visual C++ 6.0.

Podczas dystrybucji aplikacji należy zainstalować i zarejestrować .ocx dla formantu ActiveX (przy użyciu regsvr32.exe). Ponadto należy upewnić się, że komputer docelowy ma bieżące wersje następujących plików systemowych (gwiazdka wskazuje, że plik musi zostać zarejestrowany):

- Asycfilt.dll

- Comcat.dll\*

- Oleaut32.dll\*

- Olepro32.dll\*

- Stdole2.tlb

Jeśli te biblioteki DLL nie są dostępne w systemie docelowym, należy je zaktualizować przy użyciu zalecanego mechanizmu aktualizacji odpowiedniego systemu operacyjnego. Najnowsze dodatki Service Pack dla systemów operacyjnych Windows można pobrać z programu [http://windowsupdate.microsoft.com](https://windowsupdate.microsoft.com).

Podczas korzystania z formantu ActiveX, który łączy się z bazą danych, należy również replikować nazwę źródła danych na komputerze docelowym. Można to zrobić programowo za `ConfigDSN`pomocą funkcji, takich jak .

Niektóre redystrybucyjne formanty ActiveX mają dodatkowe zależności. Dla każdego pliku ocx w folderze Os\System na dysku CD produktu Visual C++ 6.0 dostępny jest również plik dep. Dla każdego pliku ocx, który chcesz redystrybuować, poszukaj jednego lub więcej wpisów USES w odpowiednim pliku dep. Jeśli plik znajduje się na liście, należy upewnić się, że plik znajduje się na komputerze docelowym. Wszystkie biblioteki DLL obsługujące plik .ocx muszą zostać zarejestrowane. (Aby program Regsvr32.exe zakończył się pomyślnie, komputer docelowy musi najpierw zawierać wszystkie biblioteki DLL, które ładuje statycznie). Ponadto jeśli biblioteka DLL, która jest wymieniona jako zależność, ma również plik dep w folderze Os\System na dysku CD visual C++ 6.0, należy również zbadać ten plik dep dla wpisów USES.

## <a name="see-also"></a>Zobacz też

[Ponowne dystrybuowanie plików programu Visual C++](redistributing-visual-cpp-files.md)
