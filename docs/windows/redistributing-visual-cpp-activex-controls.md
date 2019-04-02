---
title: Redystrybuowanie formantów ActiveX programu Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
ms.openlocfilehash: e8eba02f1a2c5706a91b85e3b20a4e4be557537b
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787466"
---
# <a name="redistributing-visual-c-activex-controls"></a>Redystrybuowanie formantów ActiveX programu Visual C++

Visual C++ 6.0 dostarcza kontrolki ActiveX, używane w aplikacjach, które następnie ponownie rozesłać. Te kontrolki znajdują się już w programie Visual C++. Na umowy licencyjne dla Visual C++ 6.0 można redystrybuować tych kontrolek, za pomocą aplikacji utworzonych w programie Visual C++.

> [!NOTE]
>  Visual C++ 6.0 nie jest już obsługiwana przez firmę Microsoft.

Aby uzyskać listę pakiet redystrybucyjny Visual C++ 6.0 formantów Zobacz Common\Redist\Redist.txt 1 dysk na dysku CD produktu Visual C++ 6.0.

Podczas dystrybucji aplikacji, należy zainstalować i zarejestrować .ocx dla formantu ActiveX (przy użyciu Regsvr32.exe). Ponadto należy się upewnić, że komputer docelowy ma aktualne wersje następujących plików systemowych (gwiazdka wskazuje, że plik musi być zarejestrowana):

- Asycfilt.dll

- Comcat.dll \*

- Oleaut32.dll \*

- Olepro32.dll \*

- Stdole2.tlb

Te biblioteki DLL nie są dostępne w systemie docelowym, należy je zaktualizować przy użyciu mechanizmu wymaganych aktualizacji odpowiedni system operacyjny. Możesz pobrać najnowsze dodatki service Pack dla systemów operacyjnych Windows z [ http://windowsupdate.microsoft.com ](https://windowsupdate.microsoft.com).

Korzystając z formantu ActiveX, który nawiązuje połączenie z bazą danych, należy również replikować nazwa źródła danych na komputerze docelowym. Można to zrobić programowo przy użyciu funkcji takich jak `ConfigDSN`.

Niektóre formanty ActiveX redystrybucyjne mają dodatkowe zależności. Dla każdego pliku .ocx w folderze Os\System na dysku CD produktu Visual C++ 6.0 jest również plik .dep. Dla każdego pliku .ocx, który chcesz wykonać ponowną dystrybucję Wyszukaj jeden lub więcej wpisów UŻYWA w odpowiedni plik .dep. Jeśli plik ma na liście, upewnij się, że plik znajduje się na komputerze docelowym. Bezpośrednio obsługuje pliku ocx muszą być zarejestrowani każdej biblioteki dll. (Dla Regsvr32.exe zakończyło się sukcesem, komputer docelowy musi zawierać wszystkie biblioteki DLL statycznie ładuje kontrolki.) Ponadto jeśli biblioteki DLL, który jest wymieniony jako zależność ma również plik .dep w folderze Os\System na dysku CD programu Visual C++ 6.0, należy zbadać również tego pliku .dep UŻYWA wpisy.

## <a name="see-also"></a>Zobacz także

[Ponowne dystrybuowanie plików programu Visual C++](redistributing-visual-cpp-files.md)
