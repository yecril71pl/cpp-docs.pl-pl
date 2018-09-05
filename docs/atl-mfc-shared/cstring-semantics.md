---
title: Cstring — semantyka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 256c71cace15a3906ac048819ab2ffdef2071ff4
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761276"
---
# <a name="cstring-semantics"></a>Cstring — semantyka

Mimo że [CString](../atl-mfc-shared/reference/cstringt-class.md) obiekty są dynamiczne obiekty, które można powiększać, mogą zachowywać się jak prosty klasy i wbudowanych typami pierwotnymi. Każdy `CString` obiekt reprezentuje unikatową wartość. `CString` obiekty należy traktować jako rzeczywisty ciągi, a nie jako wskaźnikami do ciągów.

Można przypisać jedną `CString` obiektu do drugiego. Jednak po zmodyfikowaniu jedną z dwóch `CString` obiektów innych `CString` obiekt nie jest modyfikowany, jak pokazano na poniższym przykładzie:

[!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]

Uwaga w przykładzie, dwa `CString` obiekty są traktowane jako "equal", ponieważ stanowią one ten sam ciąg znaków. `CString` Klasy przeciążenia operatora równości (`==`) do porównywania dwóch `CString` obiektów na podstawie ich wartości (zawartość) zamiast ich tożsamości (adres).

## <a name="see-also"></a>Zobacz też

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

