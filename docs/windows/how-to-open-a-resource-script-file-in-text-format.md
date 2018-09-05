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
ms.openlocfilehash: e331966c44d19f2410a59505348bcc0a37c63912
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676056"
---
# <a name="how-to-open-a-resource-script-file-in-text-format"></a>Porady: otwieranie pliku skryptu zasobu w formacie tekstowym

Mogą wystąpić sytuacje, gdy chcesz wyświetlić zawartość pliku skryptu (.rc) zasobu projektu bez konieczności otwierania zasobu, np. okno dialogowe wewnątrz jego Edytor określonego zasobu. Na przykład można wyszukać ciąg we wszystkich oknach dialogowych w pliku zasobów bez konieczności otwierania każdej z nich osobno.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

Łatwo można otworzyć pliku zasobów, w formacie tekstowym, aby wyświetlić wszystkie zasoby, zawiera i wykonywać globalne operacje obsługiwane przez Edytor tekstu.

> [!NOTE]
> Edytory zasobów bezpośrednio odczytu nie .rc lub `resource.h` plików. Kompilator zasobów kompiluje je na .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i tylko przechowuje dane symboliczne. Jak zwykłym skompilować procesu, informacje symboliczne (na przykład komentarzy) jest pomijany w procesie kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z pliku .rc, zostanie ponownie wygenerowany plik .rc (na przykład podczas zapisywania, Edytor zasobów zastąpi plików .rc i pliku resource.h). Zmiany wprowadzone w zasobach pozostaną dołączone w pliku .rc, ale komentarze zostać utracone po plik .rc jest zastępowany. Aby uzyskać informacje na temat sposobu zachowanie komentarzy, wyświetlić [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md).

### <a name="to-open-a-resource-script-file-as-text"></a>Można otworzyć pliku skryptu zasobu jako tekst

1. Z **pliku** menu wybierz opcję **Otwórz**, następnie kliknij przycisk **pliku.**

2. W **Otwórz plik** okno dialogowe, przejdź do pliku skryptu zasobów, którą chcesz wyświetlić w formacie tekstowym.

3. Zaznacz plik, a następnie kliknij strzałkę listy rozwijanej **Otwórz** przycisku (znajdujący się po prawej stronie przycisku).

4. Wybierz **Otwórz za pomocą** z menu rozwijanego.

5. W **Otwórz za pomocą** okno dialogowe, kliknij przycisk **Edytor kodu źródłowego (tekst)**.

6. Z **Otwórz jako** listy rozwijanej wybierz **tekstu**.

   Zasób, który zostanie otwarty w **kod źródłowy** edytora.

\- lub —

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik .rc.

2. Z menu skrótów wybierz polecenie **Otwórz za pomocą...** , a następnie wybierz **Edytor kodu źródłowego (tekst)**.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Edytory zasobów](../windows/resource-editors.md)