---
title: Edytowalne typy plików zasobów (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: c40f9204-f2f2-400b-9f53-53b7bf291356
ms.openlocfilehash: 9f688c144a3453c2de849b36f34f6a465e3dfeae
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905722"
---
# <a name="editable-file-types-for-resources-c"></a>Edytowalne typy plików zasobów (C++)

Można otworzyć następujących typów plików i edytowanie zasobów, które zawierają.

|Nazwa pliku|Opis|
|---------------|-----------------|
|.rc|Pliki skryptów zasobów.|
|.rct|Pliki szablonów zasobów.|
|.res|Pliki zasobów.|
|.resx|Zarządzanych plików zasobów.|
|.exe|Pliki wykonywalne.|
|.dll|Pliki bibliotek dołączanych dynamicznie.|
|.bmp, .ico, .dib i .cur|Pliki map bitowych, ikony, narzędzi i kursora.|

## <a name="files-affected-by-resource-editing"></a>Pliki uszkodzone przez edytowanie zasobów

W środowisku Visual Studio współpracuje z plików pokazano w poniższej tabeli w czasie sesji edytowania zasobów.

|Nazwa pliku|Opis|
|---------------|-----------------|
|Resource.h|Plik nagłówkowy generowane przez środowisko programistyczne; zawiera definicje symbolu. (Dołącz ten plik w kontroli źródła).|
|Filename.APS|Binarna wersja bieżącego pliku skryptu zasobów; używany do szybkiego ładowania.<br /><br /> Edytory zasobów bezpośrednio odczytu nie plików .rc lub resource.h. Kompilator zasobów kompiluje je na .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i tylko przechowuje dane symboliczne. Jak zwykłym skompilować procesu, informacje symboliczne (na przykład komentarzy) jest pomijany w procesie kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z pliku .rc, zostanie ponownie wygenerowany plik .rc (na przykład podczas zapisywania, Edytor zasobów zastąpi plików .rc i pliku resource.h). Zmiany wprowadzone w zasobach pozostaną dołączone w pliku .rc, ale komentarze zostać utracone po plik .rc jest zastępowany. Aby uzyskać informacje na temat sposobu zachowanie komentarzy, wyświetlić [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md). (Zazwyczaj nie należy używać pliku .aps w kontroli źródła.)|
|.rc|Plik skryptu zasobu, który zawiera skrypt dla zasobów w bieżącym projekcie. Ten plik jest nadpisywany przez plik .aps przy każdym zapisywaniu. (Dołącz ten plik w kontroli źródła).|

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Pliki zasobów](../windows/resource-files-visual-studio.md)