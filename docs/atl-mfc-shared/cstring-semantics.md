---
title: "Cstring — semantyki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 394e459a46003e3f1baccff7dd4c76f40b73e354
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cstring-semantics"></a>Cstring — semantyki
Mimo że [cstring —](../atl-mfc-shared/reference/cstringt-class.md) obiekty są dynamiczne obiekty, które można powiększać, działają podobnie jak wbudowanych typów pierwotnych i proste klasy. Każdy `CString` obiekt reprezentuje unikatową wartość. `CString`obiekty należy traktować jako rzeczywisty ciągi, a nie jako wskaźników do ciągów.  
  
 Należy przypisać jeden **cstring —** obiektu do innego. Jednak po zmodyfikowaniu jedną z tych dwóch `CString` obiekty innych `CString` obiektu nie jest modyfikowany, jak pokazano na poniższym przykładzie:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]  
  
 Uwaga w przykładzie który dwa `CString` obiekty są traktowane jako "równego", ponieważ stanowią one ten sam ciąg znaków. `CString` Klasy overloads operator równości (`==`) do porównania dwóch `CString` obiekty na podstawie ich wartości (wartość) zamiast tożsamości (adresu).  
  
## <a name="see-also"></a>Zobacz też  
 [Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

