---
title: Klasa CPtrList | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPtrList
dev_langs:
- C++
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 421373969beb83d033ce8ca14bd11fdb5d8dcb14
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078624"
---
# <a name="cptrlist-class"></a>Klasa CPtrList
Obsługuje listy wskaźniki typu void.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPtrList : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
 Funkcje Członkowskie `CPtrList` są podobne do funkcji Członkowskich klasy [CObList](../../mfc/reference/coblist-class.md). Ze względu na to podobieństwa, można użyć `CObList` odwołania dokumentacji charakterystykę funkcja elementu członkowskiego. Po wyświetleniu `CObject` wskaźnika jako parametr funkcji lub wartości zwracanej, Zastąp wskaźnik do **void**.  
  
 `CObject*& CObList::GetHead() const;`  
  
 na przykład umożliwia to  
  
 `void*& CPtrList::GetHead() const;`  
  
## <a name="remarks"></a>Uwagi  
 `CPtrList` zawiera `IMPLEMENT_DYNAMIC` makro do obsługi dostępu typu run-time i zrzucanie `CDumpContext` obiektu. Zrzut wskaźnika poszczególnych elementów listy, należy do co najmniej 1 należy ustawić głębokość kontekstu zrzutu.  
  
 Nie można zserializować list wskaźnika.  
  
 Gdy `CPtrList` obiekt jest usunięty lub gdy jego elementy są usuwane, są usuwane tylko wskaźniki, nie odwołują się do jednostek.  
  
 Aby uzyskać więcej informacji na temat używania `CPtrList`, zapoznaj się z artykułem [kolekcji](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CPtrList`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcoll.h  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CObList](../../mfc/reference/coblist-class.md)
