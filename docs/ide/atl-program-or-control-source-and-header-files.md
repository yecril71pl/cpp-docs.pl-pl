---
title: ATL Program lub źródło kontroli i pliki nagłówkowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95fa6fa506e4f471b90d39659b0908e2755b72b0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398706"
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

## <a name="see-also"></a>Zobacz też

[Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[Program MFC lub źródło kontroli i pliki nagłówkowe](../ide/mfc-program-or-control-source-and-header-files.md)<br>
[Projekty CLR](../ide/files-created-for-clr-projects.md)