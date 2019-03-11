---
title: Program ATL lub źródło kontroli i pliki nagłówkowe
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
ms.openlocfilehash: 9a99c3c23a79c37e90d9a041f051cfeaaff13ae2
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745014"
---
# <a name="atl-program-or-control-source-and-header-files"></a>Program ATL lub źródło kontroli i pliki nagłówkowe

Następujące pliki są tworzone podczas tworzenia projektu ATL w programie Visual Studio, w zależności od opcji wybranej dla tworzonego projektu.

Wszystkie te pliki znajdują się w *Projname* katalogu, a w folderze pliki nagłówków (.h pliki) lub pliki źródłowe (.cpp pliki) folder w Eksploratorze rozwiązań.

|Nazwa pliku|Opis|
|---------------|-----------------|
|*Projname*.h|Plik dołączania głównego, zawierający definicje interfejsu C++ i identyfikator GUID deklaracje elementy zdefiniowane w ATLSample.idl. Generowane przez MIDL podczas kompilacji.|
|*Projname*.cpp|Plik źródłowy głównego programu. Zawiera on implementacja eksportów biblioteki DLL serwera w procesie i wykonania `WinMain` dla serwera lokalnego. W przypadku usługi dodatkowo implementuje wszystkich funkcji zarządzania usługi.|
|Resource.h|Plik nagłówka dla pliku zasobów.|
|StdAfx.cpp|Dotyczy plików StdAfx.h i Atlimpl.cpp.|
|StdAfx.h|Zawiera pliki nagłówkowe biblioteki ATL.|

## <a name="see-also"></a>Zobacz także

[Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[Program MFC lub źródło kontroli i pliki nagłówkowe](../ide/mfc-program-or-control-source-and-header-files.md)<br>
[Projekty CLR](../ide/files-created-for-clr-projects.md)
