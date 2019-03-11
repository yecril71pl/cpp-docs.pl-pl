---
title: Cstring — semantyka
ms.date: 11/04/2016
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
ms.openlocfilehash: b5398f8a0f17ffcc93c7f5f6158ecc56606e9279
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750184"
---
# <a name="cstring-semantics"></a>Cstring — semantyka

Mimo że [CString](../atl-mfc-shared/reference/cstringt-class.md) obiekty są dynamiczne obiekty, które można powiększać, mogą zachowywać się jak prosty klasy i wbudowanych typami pierwotnymi. Każdy `CString` obiekt reprezentuje unikatową wartość. `CString` obiekty należy traktować jako rzeczywisty ciągi, a nie jako wskaźnikami do ciągów.

Można przypisać jedną `CString` obiektu do drugiego. Jednak po zmodyfikowaniu jedną z dwóch `CString` obiektów innych `CString` obiekt nie jest modyfikowany, jak pokazano na poniższym przykładzie:

[!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]

Uwaga w przykładzie, dwa `CString` obiekty są traktowane jako "equal", ponieważ stanowią one ten sam ciąg znaków. `CString` Klasy przeciążenia operatora równości (`==`) do porównywania dwóch `CString` obiektów na podstawie ich wartości (zawartość) zamiast ich tożsamości (adres).

## <a name="see-also"></a>Zobacz także

[Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
