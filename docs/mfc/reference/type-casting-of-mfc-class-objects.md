---
title: Rzutowanie typów obiektów klas MFC
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
ms.openlocfilehash: e3702ced83021e42ac6bf71a78efc51fa07b8be9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840495"
---
# <a name="type-casting-of-mfc-class-objects"></a>Rzutowanie typów obiektów klas MFC

Makra rzutowania typów umożliwiają rzutowanie danego wskaźnika na wskaźnik wskazujący obiekt określonej klasy, z lub bez sprawdzania, czy Rzutowanie jest dozwolone.

W poniższej tabeli wymieniono makra do rzutowania typów MFC.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Makra, które rzutowania wskaźników do obiektów klas MFC

|Nazwa|Opis|
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Rzutuje wskaźnik na wskaźnik do obiektu klasy podczas sprawdzania, czy Rzutowanie jest dozwolone.|
|[STATIC_DOWNCAST](#static_downcast)|Rzutuje wskaźnik na obiekt z jednej klasy do wskaźnika powiązanego typu. W kompilacji debugowania powoduje potwierdzenie, jeśli obiekt nie jest rodzajem typu docelowego.|

## <a name="dynamic_downcast"></a><a name="dynamic_downcast"></a> DYNAMIC_DOWNCAST

Zapewnia wygodny sposób rzutowania wskaźnika na wskaźnik do obiektu klasy podczas sprawdzania, czy Rzutowanie jest dozwolone.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>Parametry

*określonej*<br/>
Nazwa klasy.

*pointer*<br/>
Wskaźnik, który ma być rzutowany na wskaźnik do obiektu typu *Class*.

### <a name="remarks"></a>Uwagi

Makro będzie rzutować parametr *wskaźnika* na wskaźnik do obiektu typu parametru *klasy* .

Jeśli obiekt, do którego odwołuje się wskaźnik, jest "rodzajem" wskazanej klasy, makro zwraca odpowiedni wskaźnik. Jeśli nie jest to dozwolone, makro zwraca wartość NULL.

## <a name="static_downcast"></a><a name="static_downcast"></a> STATIC_DOWNCAST

Rzutuje *pObject* na wskaźnik do obiektu *class_name* .

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy, do której ma zostać rzutowane.

*pobject*<br/>
Wskaźnik, który ma być rzutowany na wskaźnik do obiektu *class_name* .

### <a name="remarks"></a>Uwagi

*pObject* musi mieć wartość null lub wskazywać obiekt klasy, która jest pochodną bezpośrednio lub pośrednio z *class_name*. W kompilacjach aplikacji z zdefiniowanym symbolem preprocesora _DEBUG, makro zostanie potwierdzone, jeśli *pObject* nie ma wartości null lub jeśli wskazuje na obiekt, który nie jest "rodzajem" klasy określonej w parametrze *Class_name* (patrz [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). W kompilacjach innych niż **_DEBUG** makro wykonuje Rzutowanie bez sprawdzania typu.

Klasa określona w parametrze *class_name* musi być pochodną `CObject` i musi używać DECLARE_DYNAMIC i IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE i IMPLEMENT_DYNCREATE, lub DECLARE_SERIAL i IMPLEMENT_SERIAL makr, jak wyjaśniono w artykule [CObject artykułu: wyprowadzanie klasy z CObject](../../mfc/deriving-a-class-from-cobject.md).

Na przykład można rzutować wskaźnik na `CMyDoc` , wywołany `pMyDoc` , na wskaźnik, aby `CDocument` użyć tego wyrażenia:

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

Jeśli nie `pMyDoc` wskazuje obiektu pochodnego bezpośrednio lub pośrednio z `CDocument` , makro zostanie potwierdzone.

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
