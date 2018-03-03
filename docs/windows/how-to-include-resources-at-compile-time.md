---
title: "Porady: dołączanie zasobów w czasie kompilacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 201985a10d0f5a58fc7d617e307d2715bf29be32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-include-resources-at-compile-time"></a>Porady: dołączanie zasobów w czasie kompilacji
Zazwyczaj jest łatwy i wygodny do pracy z domyślnego rozmieszczenia wszystkie zasoby w jednym pliku skryptu (.rc) zasobu. Jednak można dodać zasobów w innych plików do bieżącego projektu w czasie kompilacji poprzez wyszczególnienie je w **dyrektywy kompilacji** polu [zasób zawiera okno dialogowe](../windows/resource-includes-dialog-box.md).  
  
 Istnieje kilka przyczyn, które można umieścić w pliku innym niż plik .rc głównego zasobów:  
  
-   Aby dodać komentarze do instrukcji zasobów, które nie są usuwane podczas zapisywania pliku .rc.  
  
     Edytory zasobów bezpośrednio odczytu nie .rc lub resource.h plików. Kompilator zasobów kompiluje je w .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i przechowuje dane tylko symboliczne danych. Jak w zwykłym skompilować procesu, informacje, które nie jest symboliczne (na przykład komentarzy) zostaną odrzucone podczas procesu kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z plik .rc, zostanie ponownie wygenerowany plik .rc (na przykład podczas zapisywania, Edytor zasobów zastępuje plik .rc i plik resource.h). Zmiany wprowadzone w samych zasobach pozostaną dołączone w plik .rc, ale komentarze zostać utracone po plik .rc jest zastępowany.  
  
-   Zawierającego zasoby, które już zostały opracowane i przetestowane i nie trzeba zmieniać. (Wszystkie pliki, które są uwzględniane, ale nie ma rozszerzenia .rc nie będzie można edytować przez edytory zasobów).  
  
-   Aby uwzględnić zasobów, które są używane przez kilka różnych projektów lub należą do systemu kontroli wersji kodu źródłowego i w związku z tym musi istnieć w centralnej lokalizacji, w którym zmiany będzie miało wpływ na wszystkie projekty.  
  
-   Aby uwzględnić zasobów (takich jak zasoby RCDATA), które są w niestandardowym formacie. Zasoby RCDATA mogą mieć specjalnych wymagań. Na przykład nie można użyć wyrażenia jako wartości dla pola nameID. Zobacz [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] dokumentacji, aby uzyskać więcej informacji.  
  
 Jeśli masz sekcje w plikach .rc istniejących, które spełniają jeden z następujących warunków sekcji należy umieścić w jednej lub więcej oddzielnych .RC — pliki i je uwzględnić w projekcie za pomocą [zasób zawiera okno dialogowe](../windows/resource-includes-dialog-box.md). *Projectname*plik .rc2 utworzone w podkatalogu \res nowego projektu jest używany w tym celu.  
  
### <a name="to-include-resources-in-your-project-at-compile-time"></a>Aby uwzględnić zasobów w projekcie w czasie kompilacji  
  
1.  Umieść zasobów w pliku skryptu zasobu z unikatową nazwę pliku. Nie używaj *projectname*.rc, ponieważ jest to nazwa pliku używana dla pliku skryptu zasobu głównego.  
  
2.  Kliknij prawym przyciskiem myszy plik .rc (w [widok zasobów](../windows/resource-view-window.md)) i wybierz polecenie **zasobów zawiera** z menu skrótów.  
  
3.  W **dyrektywy kompilacji** Dodaj [#include](../preprocessor/hash-include-directive-c-cpp.md) dyrektywy kompilatora, aby dołączyć nowy plik zasobów w pliku głównym zasobów w środowisku programistycznym.  
  
     Zasoby w plików znajdujących się w ten sposób będą częścią pliku wykonywalnego w czasie kompilacji. Nie są oni bezpośrednio dostępne do edycji lub modyfikacji podczas pracy na plik .rc głównym projektu. Należy otworzyć dołączone .RC — pliki oddzielnie. Wszystkie pliki, które są uwzględniane, ale nie ma rozszerzenia .rc nie będzie można edytować przez edytory zasobów.  
  

  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)