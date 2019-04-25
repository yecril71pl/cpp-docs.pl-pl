---
title: Rzutowanie typów obiektów klas MFC
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.classes
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
ms.openlocfilehash: 3107b860747bc2434ae9afca39b517d8dcc9eb01
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309814"
---
# <a name="type-casting-of-mfc-class-objects"></a>Rzutowanie typów obiektów klas MFC

Typ rzutowania makra umożliwiają rzutowanie danego wskaźnika do wskaźnika, który wskazuje na obiekt określonej klasy, z lub bez sprawdzania, czy rzutowanie jest prawnych.

W poniższej tabeli wymieniono makr rzutowania typu MFC.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Makra, które rzutowanie wskaźników do obiektów klas MFC

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Rzutuje wskaźnika do wskaźnika do obiektu klasy podczas sprawdzania, jeśli rzutowanie jest dozwolony.|
|[STATIC_DOWNCAST](#static_downcast)|Rzutuje wskaźnik do obiektu z jednej klasy do wskaźnika typu powiązane. Do kompilacji debugowanej powoduje potwierdzenie, jeśli obiekt nie jest "rodzaju" na typ docelowy.|

##  <a name="dynamic_downcast"></a>  DYNAMIC_DOWNCAST

Zapewnia wygodny sposób rzutowanie wskaźnika do wskaźnika do obiektu klasy podczas sprawdzania, jeśli rzutowanie jest dozwolony.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>Parametry

*class*<br/>
Nazwa klasy.

*pointer*<br/>
Wskaźnik do być rzutowany na wskaźnik do obiektu typu *klasy*.

### <a name="remarks"></a>Uwagi

Makra zostanie rzutowania *wskaźnik* parametru na wskaźnik do obiektu *klasy* typu parametru.

Jeśli obiekt odwołuje się wskaźnik jest "rodzaju" klasy zidentyfikowanych makro zwraca odpowiednie wskaźnik. Jeśli nie jest rzutowanie prawne, makro zwraca wartość NULL.

##  <a name="static_downcast"></a>  STATIC_DOWNCAST

Rzutowania *obiekt* na wskaźnik do *class_name* obiektu.

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy rzutowany.

*pobject*<br/>
Wskaźnik, aby być rzutowany na wskaźnik do *class_name* obiektu.

### <a name="remarks"></a>Uwagi

*obiekt* musi mieć wartość NULL albo wskazać obiekt klasy, która pochodzi bezpośrednio lub pośrednio z *class_name*. W kompilacjach do aplikacji za pomocą symbol preprocesora _DEBUG zdefiniowane makro będzie potwierdzenia, jeśli *obiekt* nie ma wartości NULL, lub jeśli wskazuje na obiekt, który nie jest "rodzaju" klasa określona w *class_name*parametr (zobacz [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). W non - **_DEBUG** kompilacje, makro wykonuje rzutowanie bez sprawdzania typu.

Klasa określona w *class_name* parametru musi pochodzić od `CObject` i musi być DECLARE_DYNAMIC i IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE i IMPLEMENT_DYNCREATE, lub DECLARE_SERIAL i IMPLEMENT_ SERIAL makra, jak wyjaśniono w artykule [klasa CObject: Wyprowadzanie klasy z obiektu CObject](../../mfc/deriving-a-class-from-cobject.md).

Na przykład może rzutować wskaźnik do `CMyDoc`, co jest nazywane `pMyDoc`, wskaźnik do `CDocument` za pomocą następującego wyrażenia:

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

Jeśli `pMyDoc` nie wskazuje na obiekt, który pochodzi bezpośrednio lub pośrednio z `CDocument`, makro będzie potwierdzenia.

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
