---
title: Redystrybuowanie formantów ActiveX programu Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b770bbacca06c6edfb3b9b4eda53fc7be8a7ae0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="redistributing-visual-c-activex-controls"></a>Redystrybuowanie kontrolek ActiveX programu Visual C++
Visual C++ 6.0 dostarcza formantów ActiveX, używanych w aplikacjach, które następnie ponownie rozesłać. Formanty znajdują się już w programie Visual C++. Na umów licencjonowania Visual C++ 6.0 można ponownie rozesłać tych kontrolek z aplikacji utworzonych w programie Visual C++.  
  
> [!NOTE]
>  Visual C++ 6.0 nie jest już obsługiwana przez firmę Microsoft.  
  
 Lista pakietu redystrybucyjnego Visual C++ 6.0 ActiveX formantów Zobacz Common\Redist\Redist.txt 1 dysku CD produktu Visual C++ 6.0.  
  
 Podczas dystrybucji aplikacji, należy zainstalować i zarejestrować .ocx dla formantu ActiveX (przy użyciu Regsvr32.exe). Ponadto należy upewnić się, że komputer docelowy ma bieżących wersjach następujących plików systemowych (gwiazdkę oznacza, że plik powinien być zarejestrowany):  
  
-   Asycfilt.dll  
  
-   Plik comcat.dll *  
  
-   Oleaut32.dll *  
  
-   Olepro32.dll *  
  
-   Stdole2.tlb  
  
 Te biblioteki DLL nie są dostępne na komputerze docelowym, należy je zaktualizować przy użyciu mechanizmu wymaganych aktualizacji odpowiedni system operacyjny. Możesz pobrać najnowszymi dodatkami service Pack dla systemu operacyjnego z [ http://windowsupdate.microsoft.com ](http://windowsupdate.microsoft.com).  
  
 Jeśli aplikacja korzysta z jednego z kontrolki ActiveX, które nawiązuje połączenie z bazą danych, musisz mieć Microsoft Data Access Components (MDAC) zainstalowany na komputerze docelowym. Aby uzyskać więcej informacji, zobacz [redystrybuowanie plików obsługi baz danych](../ide/redistributing-database-support-files.md).  
  
 Korzystając z formantu ActiveX, który nawiązuje połączenie z bazą danych, należy replikować nazwa źródła danych na komputerze docelowym. Można to zrobić programowo funkcje takie jak `ConfigDSN`.  
  
 Niektóre pakietu redystrybucyjnego kontrolki ActiveX ma dodatkowe zależności. Dla każdego pliku .ocx w folderze Os\System na dysku CD produktu Visual C++ 6.0 jest również plik .dep. Dla każdego pliku ocx, który chcesz ponownie rozesłać Wyszukaj jeden lub więcej wpisów UŻYWA w odpowiedni plik .dep. Jeśli plik jest wyświetlana, upewnij się, że plik znajduje się na komputerze docelowym. Wszystkie biblioteki DLL bezpośrednio obsługi pliku ocx należy zarejestrować. (Dla Regsvr32.exe została wykonana pomyślnie, na komputerze docelowym musi najpierw zawiera wszystkie kontrolki statycznie ładuje bibliotek DLL). Ponadto jeśli bibliotekę DLL, która jest wymieniony jako zależność ma również plik .dep w folderze Os\System na dysku CD programu Visual C++ 6.0, musi także zbadać tego pliku .dep UŻYWA wpisy.  
  
## <a name="see-also"></a>Zobacz też  
 [Ponowne dystrybuowanie plików programu Visual C++](../ide/redistributing-visual-cpp-files.md)