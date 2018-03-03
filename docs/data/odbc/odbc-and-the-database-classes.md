---
title: ODBC i klasy baz danych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e3041a4fc027a8786fb62db7df6eaf486633ce97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-and-the-database-classes"></a>ODBC i klasy baz danych
Klasy baz danych MFC ODBC Hermetyzowanie wywołania funkcji ODBC API będzie zwykle należy samodzielnie w element członkowski funkcji [cdatabase —](../../mfc/reference/cdatabase-class.md) i [crecordset —](../../mfc/reference/crecordset-class.md) klasy. Na przykład złożonych sekwencji wywołania ODBC, powiązanie zwróconych rekordów do lokalizacji przechowywania, obsługa błędów i inne operacje są zarządzane dla Ciebie przez klasy baz danych. W związku z tym użyj znacznie prostsze interfejsu klasy do modyfikowania rekordów przez obiekt zestawu rekordów.  
  
> [!NOTE]
>  ODBC — źródła danych są dostępne za pośrednictwem klas MFC ODBC, zgodnie z opisem w tym temacie lub za pośrednictwem klas MFC obiekt DAO (Data Access).  
  
 Mimo że klas baz danych Hermetyzowanie funkcji ODBC, nie zapewniają mapowanie jeden do jednego funkcji interfejsu API ODBC. Klasy baz danych zapewnia wyższy poziom abstrakcji modelowana po znalezieniu obiektów dostępu do danych programu Microsoft Access i Microsoft Visual Basic. Aby uzyskać więcej informacji, zobacz [ODBC i MFC](../../data/odbc/odbc-and-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy ODBC](../../data/odbc/odbc-basics.md)