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
ms.openlocfilehash: 4595ea9ce27c40fb798ac050ce456c4d43b2cacb
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33328090"
---
# <a name="precompiled-header-files"></a>Prekompilowane pliki nagłówka
Te pliki są używane do tworzenia prekompilowanego pliku nagłówkowego *nazwa_projektu.nazwa_modułu.nazwa_procedury*.pch i wstępnie skompilowane typy plików Stdafx.obj.  
  
 Te pliki znajdują się w *nazwa_projektu.nazwa_modułu.nazwa_procedury* katalogu. W Eksploratorze rozwiązań Stdafx.h znajduje się w folderze pliki nagłówkowe, a Stdafx.cpp znajduje się w folderze plików źródłowych.  
  
|Nazwa pliku|Opis|  
|---------------|-----------------|  
|Stdafx.h|Dołączanego pliku dla standardowych systemowych plików dołączanych i pliki nagłówkowe specyficznego dla projektu, które są często używane, ale są rzadko zmieniane.<br /><br /> Nie należy zdefiniować lub usuń wszelkie makra _AFX_NO_XXX w pliku stdafx.h; zobacz artykuł bazy wiedzy Knowledge Base "PRB: powodować problemy podczas definiowania _AFX_NO_XXX". Artykuły bazy wiedzy można znaleźć w bibliotece MSDN lub na [http:// support.microsoft.com/](http://%20support.microsoft.com/).|  
|Stdafx.cpp|Zawiera dyrektywy preprocesora `#include "stdafx.h"` i dodaje Dołącz pliki dla wstępnie skompilowane typy. Wstępnie skompilowanych plików dowolnego typu, w tym pliki nagłówkowe obsługuje szybsze kompilacji, ograniczając kompilacji tylko do tych plików, które tego wymagają. Po utworzeniu projektu po raz pierwszy zauważyć znacznie szybsze tworzenie razy w kolejnych kompilacjach z powodu obecności pliki prekompilowanego nagłówka.|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Praca z właściwościami projektu](../ide/working-with-project-properties.md)