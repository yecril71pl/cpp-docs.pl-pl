---
title: 'Porady: otwieranie pliku skryptu zasobu w formacie tekstowym | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resource
dev_langs:
- C++
helpviewer_keywords:
- resource script files, opening in text format
- .rc files, opening in text format
- rc files, opening in text format
ms.assetid: 0bc57527-f53b-40c9-99a9-4dcbc5c9af57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 345171742f979e488c6a4bb48cf1b57e4bb2f164
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018113"
---
# <a name="how-to-open-a-resource-script-file-in-text-format"></a>Porady: otwieranie pliku skryptu zasobu w formacie tekstowym
Mogą wystąpić sytuacje, gdy chcesz wyświetlić zawartość pliku skryptu (.rc) zasobu projektu bez konieczności otwierania zasobu, np. okno dialogowe wewnątrz jego Edytor określonego zasobu. Na przykład można wyszukać ciąg we wszystkich oknach dialogowych w pliku zasobów bez konieczności otwierania każdej z nich osobno.  
  
> [!NOTE]
>  Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).  
  
 Łatwo można otworzyć pliku zasobów, w formacie tekstowym, aby wyświetlić wszystkie zawarte w niej zasoby i wykonywać globalne operacje obsługiwane przez [edytora tekstów](http://msdn.microsoft.com/508e1f18-99d5-48ad-b5ad-d011b21c6ab1).  
  
> [!NOTE]
>  Edytory zasobów bezpośrednio odczytu nie .rc lub `resource.h` plików. Kompilator zasobów kompiluje je na .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i tylko przechowuje dane symboliczne. Jak zwykłym skompilować procesu, informacje symboliczne (na przykład komentarzy) jest pomijany w procesie kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z pliku .rc, zostanie ponownie wygenerowany plik .rc (na przykład podczas zapisywania, Edytor zasobów zastąpi plików .rc i pliku resource.h). Zmiany wprowadzone w zasobach pozostaną dołączone w pliku .rc, ale komentarze zostać utracone po plik .rc jest zastępowany. Aby uzyskać informacje na temat sposobu zachowanie komentarzy, wyświetlić [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md).  
  
### <a name="to-open-a-resource-script-file-as-text"></a>Można otworzyć pliku skryptu zasobu jako tekst  
  
1.  Z **pliku** menu wybierz opcję **Otwórz**, następnie kliknij przycisk **pliku.**  
  
2.  W **Otwórz plik** okno dialogowe, przejdź do pliku skryptu zasobów, którą chcesz wyświetlić w formacie tekstowym.  
  
3.  Zaznacz plik, a następnie kliknij strzałkę listy rozwijanej **Otwórz** przycisku (znajdujący się po prawej stronie przycisku).  
  
4.  Wybierz **Otwórz za pomocą** z menu rozwijanego.  
  
5.  W **Otwórz za pomocą** okno dialogowe, kliknij przycisk **Edytor kodu źródłowego (tekst)**.  
  
6.  Z **Otwórz jako** listy rozwijanej wybierz **tekstu**.  
  
     Zasób, który zostanie otwarty w **kod źródłowy** edytora.  
  
 \- lub —  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik .rc.  
  
2.  Z menu skrótów wybierz polecenie **Otwórz za pomocą...** , a następnie wybierz **Edytor kodu źródłowego (tekst)**.  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)