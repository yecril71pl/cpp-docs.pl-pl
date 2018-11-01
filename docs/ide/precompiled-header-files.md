---
title: Prekompilowane pliki nagłówka
ms.date: 11/04/2016
f1_keywords:
- stdafx.h
helpviewer_keywords:
- stdafx.h
- PCH files, file descriptions
- .pch files, file descriptions
- precompiled header files, file descriptions
- stdafx.cpp
ms.assetid: 8228d87a-5609-41f3-9697-b16094c000e5
ms.openlocfilehash: fed583464aa172887b80a8551adf86e02a76d210
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643212"
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