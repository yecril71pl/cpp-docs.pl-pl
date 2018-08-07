---
title: 'Porady: dołączanie zasobów w czasie kompilacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
dev_langs:
- C++
helpviewer_keywords:
- compiling source code, including resources
- comments [C++], compiled files
- resources [Visual Studio], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 856d448b096910c322750eccc7447689b08b328e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571345"
---
# <a name="how-to-include-resources-at-compile-time"></a>Porady: dołączanie zasobów w czasie kompilacji
Zazwyczaj jest łatwe i wygodne do pracy z domyślnym rozmieszczeniu wszystkich zasobów w jednym pliku skryptu (.rc) zasobu. Jednak możesz dodać zasoby w innych plikach do bieżącego projektu w czasie kompilacji przez wymienienie ich w **dyrektywy czasu kompilacji** pole w [zasób zawiera okno dialogowe](../windows/resource-includes-dialog-box.md).  
  
 Istnieje kilka przyczyn, które można umieścić zasoby w pliku innych niż plik .rc główne:  
  
-   Aby dodać komentarze do instrukcji zasobów, które nie zostaną usunięte podczas zapisywania pliku .rc.  
  
     Edytory zasobów bezpośrednio odczytu nie plików .rc lub resource.h. Kompilator zasobów kompiluje je na .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i tylko przechowuje dane symboliczne. Jak zwykłym skompilować procesu, informacje symboliczne (na przykład komentarzy) jest pomijany w procesie kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z pliku .rc, zostanie ponownie wygenerowany plik .rc (na przykład podczas zapisywania, Edytor zasobów zastąpi plików .rc i pliku resource.h). Zmiany wprowadzone w zasobach pozostaną dołączone w pliku .rc, ale komentarze zostać utracone po plik .rc jest zastępowany.  
  
-   Aby dołączyć zasoby, które już opracowany i przetestowany i nie ma potrzeby dalszej modyfikacji. (Wszystkie pliki, które są uwzględniane, ale nie ma rozszerzenia .rc nie będzie można edytować za pomocą edytory zasobów).  
  
-   Aby dołączyć zasoby, które są używane przez kilku różnych projektów lub należą do systemu kontroli wersji kodu źródłowego, a więc muszą znajdować się w centralnej lokalizacji, w którym zmiany będzie miało wpływ na wszystkie projekty.  
  
-   Aby dołączyć zasoby (na przykład zasoby RCDATA), które znajdują się w niestandardowym formacie. Zasoby RCDATA mogą mieć specjalne wymagania. Na przykład nie można użyć wyrażenia jako wartości dla pola nameID. Zobacz [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] dokumentacji, aby uzyskać więcej informacji.  
  
 Jeśli masz sekcje w istniejących plikach .rc, które spełniają dowolne z tych warunków sekcje należy umieszczać w jednym lub więcej oddzielnych plików .rc i umieszczone w projekcie za pomocą [zasób zawiera okno dialogowe](../windows/resource-includes-dialog-box.md). *Projectname*.rc2 utworzone w podkatalogu \res nowy projekt służy do tego celu.  
  
### <a name="to-include-resources-in-your-project-at-compile-time"></a>Aby dołączyć zasoby do projektu w czasie kompilacji  
  
1.  Umieść zasoby w pliku skryptu zasobu przy użyciu unikatowej nazwy pliku. Nie używaj *projectname*.rc, ponieważ jest to nazwa pliku używany dla pliku skryptu zasobu głównego.  
  
2.  Kliknij prawym przyciskiem myszy plik .rc (w [widok zasobów](../windows/resource-view-window.md)) i wybierz polecenie **zasób zawiera** z menu skrótów.  
  
3.  W **dyrektywy czasu kompilacji** Dodaj [#include](../preprocessor/hash-include-directive-c-cpp.md) dyrektywy kompilatora, które mają zostać objęte nowego pliku zasobu z głównego pliku zasobów w środowisku programistycznym.  
  
     Zasoby z plików znajdujących się w ten sposób stają się częścią pliku wykonywalnego w czasie kompilacji. Nie są one bezpośrednio dostępne do edycji lub modyfikacji podczas pracy w pliku .rc głównego projektu. Musisz otworzyć pliki .rc dołączony oddzielnie. Wszystkie pliki, które są uwzględniane, ale nie ma rozszerzenia .rc, nie będzie można edytować za pomocą edytory zasobów.  
  
## <a name="requirements"></a>Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)