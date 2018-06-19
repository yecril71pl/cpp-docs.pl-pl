---
title: Typ rzutowania obiektów klas MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 217be53a78a65a0f617438127b922b20c950853d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371164"
---
# <a name="type-casting-of-mfc-class-objects"></a>Rzutowanie typów obiektów klas MFC
Typ rzutowania makra umożliwiają można rzutować danego wskaźnika do wskaźnika, który wskazuje na obiekt określonej klasy, z lub bez sprawdzenia, czy rzutowanie jest dozwolony.  
  
 W poniższej tabeli wymieniono makra rzutowanie typu MFC.  
  
### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Makra, które rzutowanie wskaźników do obiektów klas MFC  
  
|||  
|-|-|  
|[DYNAMIC_DOWNCAST —](#dynamic_downcast)|Rzutuje wskaźnik na wskaźnik do obiektu klasy podczas sprawdzania, jeśli rzutowanie jest dozwolony.|  
|[STATIC_DOWNCAST —](#static_downcast)|Rzutuje wskaźnik do obiektu z jedną klasę do wskaźnikiem powiązanego typu. W kompilację debugowania powoduje, że **ASSERT** Jeśli obiekt nie jest "rodzaju" typ docelowy.|  
  
##  <a name="dynamic_downcast"></a>  DYNAMIC_DOWNCAST —  
 Stanowi wygodny sposób można rzutować wskaźnika do wskaźnika do obiektu klasy podczas sprawdzania, jeśli rzutowanie jest dozwolony.  
  
```   
DYNAMIC_DOWNCAST(class, pointer)  
```  
  
### <a name="parameters"></a>Parametry  
 `class`  
 Nazwa klasy.  
  
 `pointer`  
 Wskaźnik można rzutować na wskaźnik do obiektu typu `class`.  
  
### <a name="remarks"></a>Uwagi  
 Makra będzie rzutowania `pointer` parametru na wskaźnik do obiektu `class` typ parametru.  
  
 Jeśli obiekt odwołuje się wskaźnik myszy jest "rodzaju" klasy zidentyfikowanych makra zwraca odpowiednie wskaźnika. Jeśli nie jest dozwolonym rzutowania, zwraca makra **NULL**.  
  
##  <a name="static_downcast"></a>  STATIC_DOWNCAST —  
 Rzutowania *pobject* na wskaźnik do *class_name* obiektu.  
  
```   
STATIC_DOWNCAST(class_name, pobject)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa klasy jest rzutowany.  
  
 *pobject*  
 Wskaźnik można rzutować na wskaźnik do *class_name* obiektu.  
  
### <a name="remarks"></a>Uwagi  
 *pobject* muszą albo być **NULL**, lub wskaż obiekt klasy, która pochodzi bezpośrednio lub pośrednio z *class_name*. W kompilacjach aplikacji za pomocą **_DEBUG** będzie makra zdefiniowany symbol preprocesora, **ASSERT** Jeśli *pobject* nie jest **NULL**, lub wskazuje na obiekt, który nie jest "rodzaju" klasa określona w *class_name* parametr (zobacz [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). W inną niż **_DEBUG** kompilacji, makro wykonuje rzutowanie bez sprawdzania typu.  
  
 Klasa określona w *class_name* parametru musi być pochodną `CObject` i musi być `DECLARE_DYNAMIC` i `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` i `IMPLEMENT_DYNCREATE`, lub `DECLARE_SERIAL` i `IMPLEMENT_SERIAL`makra, jak opisano w artykule [klasa CObject: wyprowadzanie klasy z obiektu CObject](../../mfc/deriving-a-class-from-cobject.md).  
  
 Na przykład można rzutować wskaźnika do `CMyDoc`o nazwie `pMyDoc`, na wskaźnik do **CDocument** przy użyciu tego wyrażenia:  
  
 [!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]  
  
 Jeśli `pMyDoc` nie wskazuje na obiekt pochodzi bezpośrednio lub pośrednio od **CDocument**, będzie makra **ASSERT**.  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
