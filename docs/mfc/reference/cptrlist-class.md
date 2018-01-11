---
title: Klasa CPtrList | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CPtrList
dev_langs: C++
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d7e69c8c0d80fea2720ea436bf0bff796ae57a60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cptrlist-class"></a>Klasa CPtrList
Obsługuje listy wskaźniki typu void.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPtrList : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
 Funkcje Członkowskie `CPtrList` są podobne do funkcji Członkowskich klasy [CObList](../../mfc/reference/coblist-class.md). Ze względu na to podobieństwa, można użyć `CObList` odwołania dokumentacji charakterystykę funkcja elementu członkowskiego. Po wyświetleniu `CObject` wskaźnika jako parametr funkcji lub wartości zwracanej, Zastąp wskaźnik do `void`.  
  
 `CObject*& CObList::GetHead() const;`  
  
 na przykład umożliwia to  
  
 `void*& CPtrList::GetHead() const;`  
  
## <a name="remarks"></a>Uwagi  
 `CPtrList`zawiera `IMPLEMENT_DYNAMIC` makro do obsługi dostępu typu run-time i zrzucanie `CDumpContext` obiektu. Zrzut wskaźnika poszczególnych elementów listy, należy do co najmniej 1 należy ustawić głębokość kontekstu zrzutu.  
  
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
