---
title: Pliki uszkodzone przez zasób do edycji (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/18/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource editing
- resources [C++], editing
ms.assetid: d0820df1-ba84-40ac-bce9-29ea5ee7e3f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b70a24e77e581ebab792d9fca4d7d1a3bd8db12
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316279"
---
# <a name="files-affected-by-resource-editing-c"></a>Pliki uszkodzone przez zasób do edycji (C++)

W środowisku Visual Studio współpracuje z plików pokazano w poniższej tabeli w czasie sesji edytowania zasobów.

|Nazwa pliku|Opis|
|---------------|-----------------|
|Resource.h|Plik nagłówkowy generowane przez środowisko programistyczne; zawiera definicje symbolu. (Dołącz ten plik w kontroli źródła).|
|Filename.APS|Binarna wersja bieżącego pliku skryptu zasobów; używany do szybkiego ładowania.<br /><br /> Edytory zasobów bezpośrednio odczytu nie plików .rc lub resource.h. Kompilator zasobów kompiluje je na .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i tylko przechowuje dane symboliczne. Jak zwykłym skompilować procesu, informacje symboliczne (na przykład komentarzy) jest pomijany w procesie kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z pliku .rc, zostanie ponownie wygenerowany plik .rc (na przykład podczas zapisywania, Edytor zasobów zastąpi plików .rc i pliku resource.h). Zmiany wprowadzone w zasobach pozostaną dołączone w pliku .rc, ale komentarze zostać utracone po plik .rc jest zastępowany. Aby uzyskać informacje na temat sposobu zachowanie komentarzy, wyświetlić [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md). (Zazwyczaj nie należy używać pliku .aps w kontroli źródła.)|
|.RC|Plik skryptu zasobu, który zawiera skrypt dla zasobów w bieżącym projekcie. Ten plik jest nadpisywany przez plik .aps przy każdym zapisywaniu. (Dołącz ten plik w kontroli źródła).|

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Pliki zasobów](../windows/resource-files-visual-studio.md)