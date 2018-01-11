---
title: "Typ rzutowania obiektów klas MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros.classes
dev_langs: C++
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fc887ad855b00b525c74b66bfc70f2adb3312e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="type-casting-of-mfc-class-objects"></a>Rzutowanie typów obiektów klas MFC
Typ rzutowania makra umożliwiają można rzutować danego wskaźnika do wskaźnika, który wskazuje na obiekt określonej klasy, z lub bez sprawdzenia, czy rzutowanie jest dozwolony.  
  
 W poniższej tabeli wymieniono makra rzutowanie typu MFC.  
  
### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Makra, które rzutowanie wskaźników do obiektów klas MFC  
  
|||  
|-|-|  
|[DYNAMIC_DOWNCAST —](#dynamic_downcast)|Rzutuje wskaźnik na wskaźnik do obiektu klasy podczas sprawdzania, jeśli rzutowanie jest dozwolony.|  
|[STATIC_DOWNCAST —](#static_downcast)|Rzutuje wskaźnik do obiektu z jedną klasę do wskaźnikiem powiązanego typu. W kompilację debugowania powoduje, że **ASSERT** Jeśli obiekt nie jest "rodzaju" typ docelowy.|  
  
##  <a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST —  
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
  
##  <a name="static_downcast"></a>STATIC_DOWNCAST —  
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
