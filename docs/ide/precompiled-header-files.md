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
ms.openlocfilehash: 8d2e2bab9da3d19347577f0b1d1e8ab2ed6bb0dc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404023"
---
# <a name="precompiled-header-files"></a>Prekompilowane pliki nagłówka

Te pliki są używane do tworzenia prekompilowanego pliku nagłówkowego *Projname*.pch i wstępnie skompilowane typy plików Stdafx.obj.

Te pliki znajdują się w *Projname* katalogu. W oknie Eksploratora rozwiązań Stdafx.h znajduje się w folderze plików nagłówkowych i Stdafx.cpp znajduje się w folderze plików źródłowych.

|Nazwa pliku|Opis|
|---------------|-----------------|
|stdafx.h|Plik dołączania dla standardowych systemowych plików dołączanych i pliki nagłówkowe specyficzne dla projektu, które są często używane, ale są rzadko zmieniane.<br /><br /> Nie należy zdefiniować lub Usuń definicje, żadnego z makr _AFX_NO_XXX w pliku stdafx.h; zobacz artykuł bazy wiedzy Knowledge Base "PRB: wystąpić problemy podczas definiowania _AFX_NO_XXX". Można znaleźć artykuły bazy wiedzy w bibliotece MSDN lub na [http:// support.microsoft.com/](http://%20support.microsoft.com/).|
|stdafx.cpp|Zawiera dyrektywy preprocesora `#include "stdafx.h"` i dodaje uwzględnianie plików na potrzeby wstępnie skompilowane typy. Prekompilowane pliki dowolnego typu, w tym pliki nagłówków obsługuje szybsze czasy kompilacji przez ograniczenie możliwości wykonywania kompilacji tylko do tych plików, które tego wymagają. Po skompilowaniu projektu po raz pierwszy można zauważyć, znacznie szybciej tworzyć razy w kolejnych kompilacjach z powodu obecności plików wstępnie skompilowanego nagłówka.|

## <a name="see-also"></a>Zobacz też

[Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[Praca z właściwościami projektu](../ide/working-with-project-properties.md)