---
title: Prekompilowanych plików nagłówka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- stdafx.h
dev_langs:
- C++
helpviewer_keywords:
- stdafx.h
- PCH files, file descriptions
- .pch files, file descriptions
- precompiled header files, file descriptions
- stdafx.cpp
ms.assetid: 8228d87a-5609-41f3-9697-b16094c000e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d93486d8df8cdb8bc253a0e71037f4e2ddf9e128
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890482"
---
# <a name="precompiled-header-files"></a>Prekompilowane pliki nagłówka

Te pliki są używane do tworzenia prekompilowanego pliku nagłówkowego *Projname*.pch i wstępnie skompilowane typy plików Stdafx.obj.

Te pliki znajdują się w *Projname* katalogu. W oknie Eksploratora rozwiązań Stdafx.h znajduje się w folderze plików nagłówkowych i Stdafx.cpp znajduje się w folderze plików źródłowych.

|Nazwa pliku|Opis|
|---------------|-----------------|
|stdafx.h|Plik dołączania dla standardowych systemowych plików dołączanych i pliki nagłówkowe specyficzne dla projektu, które są często używane, ale są rzadko zmieniane.<br /><br /> Nie należy zdefiniować lub Usuń definicje, żadnego z makr _AFX_NO_XXX w pliku stdafx.h.|
|stdafx.cpp|Zawiera dyrektywy preprocesora `#include "stdafx.h"` i dodaje uwzględnianie plików na potrzeby wstępnie skompilowane typy. Prekompilowane pliki dowolnego typu, w tym pliki nagłówków obsługuje szybsze czasy kompilacji przez ograniczenie możliwości wykonywania kompilacji tylko do tych plików, które tego wymagają. Po skompilowaniu projektu po raz pierwszy można zauważyć, znacznie szybciej tworzyć razy w kolejnych kompilacjach z powodu obecności plików wstępnie skompilowanego nagłówka.|

## <a name="see-also"></a>Zobacz też

[Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[Praca z właściwościami projektu](../ide/working-with-project-properties.md)