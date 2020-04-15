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
ms.openlocfilehash: 953acc32c3510b31c265f2d64d0a013f6dee06cc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372892"
---
# <a name="type-casting-of-mfc-class-objects"></a>Rzutowanie typów obiektów klas MFC

Makra rzutowania typu umożliwiają rzutowanie danego wskaźnika na wskaźnik wskazujący obiekt określonej klasy, z lub bez sprawdzania, czy rzutowanie jest legalne.

W poniższej tabeli wymieniono makra rzutowania typu MFC.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Makra, które rzutuje wskaźniki do obiektów klasy MFC

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Rzutuje wskaźnik do wskaźnika do obiektu klasy podczas sprawdzania, czy rzutowanie jest legalne.|
|[STATIC_DOWNCAST](#static_downcast)|Rzutuje wskaźnik do obiektu z jednej klasy do wskaźnika powiązanego typu. W kompilacji debugowania powoduje ASSERT, jeśli obiekt nie jest "rodzaj" typu docelowego.|

## <a name="dynamic_downcast"></a><a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST

Zapewnia przydatny sposób rzutowania wskaźnika do wskaźnika do obiektu klasy podczas sprawdzania, czy rzutowanie jest legalne.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>Parametry

*class*<br/>
Nazwa klasy.

*pointer*<br/>
Wskaźnik, który ma być rzutowy na wskaźnik do obiektu *klasy*typu .

### <a name="remarks"></a>Uwagi

Makro przerzucy parametr *wskaźnika* na wskaźnik do obiektu typu parametru *klasy.*

Jeśli obiekt, do którego odwołuje się wskaźnik, jest "rodzajem" zidentyfikowanej klasy, makro zwraca odpowiedni wskaźnik. Jeśli nie jest to rzutowanie prawne, makro zwraca wartość NULL.

## <a name="static_downcast"></a><a name="static_downcast"></a>STATIC_DOWNCAST

Rzutuje *pobject* do wskaźnika do *obiektu class_name.*

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy, do która jest rzutowana.

*Pobject*<br/>
Wskaźnik, który ma być rzutowy na wskaźnik do *obiektu class_name.*

### <a name="remarks"></a>Uwagi

*pobject* musi mieć wartość NULL lub wskazywać obiekt klasy, który jest uzyskiwane bezpośrednio lub pośrednio z *class_name*. W kompilacjach aplikacji z zdefiniowanym symbolem preprocesora _DEBUG makro będzie potwierdzać, jeśli *pobject* nie ma wartości NULL lub jeśli wskazuje na obiekt, który nie jest "rodzajem" klasy określonej w *parametrze class_name* (patrz [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). W kompilacjach **innych niż _DEBUG** makro wykonuje rzutowanie bez sprawdzania typu.

Klasa określona w *parametrze class_name* musi pochodzić z `CObject` DECLARE_DYNAMIC i IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE i IMPLEMENT_DYNCREATE lub makr DECLARE_SERIAL i IMPLEMENT_SERIAL, jak wyjaśniono w artykule [CObject Klasa: Pochodna klasy z CObject](../../mfc/deriving-a-class-from-cobject.md).

Na przykład można rzutować `CMyDoc`wskaźnik `pMyDoc`do , wywoływane , do wskaźnika do `CDocument` korzystania z tego wyrażenia:

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

Jeśli `pMyDoc` nie wskazuje obiektu pochodzącego bezpośrednio lub `CDocument`pośrednio z , makro będzie ASSERT.

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
