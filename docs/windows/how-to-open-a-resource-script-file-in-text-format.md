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
ms.openlocfilehash: 14af857d7727ee8df13a9eb6c438342007252950
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-open-a-resource-script-file-in-text-format"></a>Porady: otwieranie pliku skryptu zasobu w formacie tekstowym
Może to być razy, jeśli chcesz wyświetlić zawartość pliku skryptu (.rc) zasobu projektu bez konieczności otwierania zasobu, na przykład okno dialogowe, w edytorze jego określonego zasobu. Można na przykład wyszukiwanie ciągu we wszystkich oknach dialogowych w pliku zasobów bez konieczności otwierania każdego z nich osobno.  
  
> [!NOTE]
>  Jeśli projekt nie zawiera już plik .rc, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).  
  
 Łatwo można otworzyć pliku zasobów w formacie tekstowym, aby wyświetlić wszystkie zasoby, które zawiera i wykonywać globalne operacje obsługiwane przez [Edytor tekstu](http://msdn.microsoft.com/en-us/508e1f18-99d5-48ad-b5ad-d011b21c6ab1).  
  
> [!NOTE]
>  Edytory zasobów bezpośrednio odczytu nie .rc lub resource.h plików. Kompilator zasobów kompiluje je w .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i przechowuje dane tylko symboliczne danych. Jak w zwykłym skompilować procesu, informacje, które nie jest symboliczne (na przykład komentarzy) zostaną odrzucone podczas procesu kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z plik .rc, zostanie ponownie wygenerowany plik .rc (na przykład podczas zapisywania, Edytor zasobów zastępuje plik .rc i plik resource.h). Zmiany wprowadzone w samych zasobach pozostaną dołączone w plik .rc, ale komentarze zostać utracone po plik .rc jest zastępowany. Aby uzyskać informacje na temat sposobu Zachowaj komentarze, zobacz [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md).  
  
### <a name="to-open-a-resource-script-file-as-text"></a>Aby otworzyć pliku skryptu zasobu jako tekst  
  
1.  Z **pliku** menu wybierz **Otwórz**, następnie kliknij przycisk **pliku.**  
  
2.  W **Otwórz plik** okno dialogowe, przejdź do pliku skryptu zasobu, który chcesz wyświetlić w formacie tekstowym.  
  
3.  Zaznacz plik, a następnie kliknij strzałkę listy rozwijanej w **Otwórz** przycisk (znajdujący się po prawej stronie przycisku).  
  
4.  Wybierz **Otwórz za pomocą** z menu rozwijanego.  
  
5.  W **Otwórz za pomocą** okno dialogowe, kliknij przycisk **edytora kodu źródłowego (tekst)**.  
  
6.  Z **Otwórz jako** listy rozwijanej wybierz **tekstu**.  
  
     Zasób zostanie otwarty w edytorze kodu źródłowego.  
  
 \- lub -  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik .rc.  
  
2.  Z menu skrótów wybierz **Otwórz za pomocą...** , a następnie wybierz pozycję **edytora kodu źródłowego (tekst)**.  
  

  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)