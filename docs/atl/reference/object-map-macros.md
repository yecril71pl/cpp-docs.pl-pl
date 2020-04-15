---
title: Makra mapy obiektów
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 66a418019ba506a5832c8e3ad86a3764c1186df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326214"
---
# <a name="object-map-macros"></a>Makra mapy obiektów

Te makra definiują mapy obiektów i wpisy.

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Umożliwia określenie opisu tekstowego obiektu klasy, który zostanie wprowadzony do mapy obiektu.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Wprowadza obiekt ATL do mapy obiektu, aktualizuje rejestr i tworzy wystąpienie obiektu.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Umożliwia określenie, że obiekt powinien zostać zarejestrowany i zainicjowany, ale nie `CoCreateInstance`powinien być można go tworzyć zewnętrznie za pośrednictwem obiektu .|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="declare_object_description"></a><a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION

Umożliwia określenie opisu tekstowego obiektu klasy.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Opis obiektu klasy.

### <a name="remarks"></a>Uwagi

ATL wprowadza ten opis do mapy obiektu za pośrednictwem [makra OBJECT_ENTRY_AUTO.](#object_entry_auto)

DECLARE_OBJECT_DESCRIPTION implementuje `GetObjectDescription` funkcję, której można użyć do zastąpienia [metody CComCoClass::GetObjectDescription.](ccomcoclass-class.md#getobjectdescription)

Funkcja `GetObjectDescription` jest wywoływana przez `IComponentRegistrar::GetComponents`. `IComponentRegistrar`to interfejs automatyzacji, który umożliwia rejestrowanie i wyrejestrowywać poszczególne składniki w biblioteki DLL. Podczas tworzenia obiektu rejestratora składników za pomocą Kreatora projektów ATL kreator `IComponentRegistrar` automatycznie zaimplementuje interfejs. `IComponentRegistrar`jest zwykle używany przez serwer transakcji firmy Microsoft.

Aby uzyskać więcej informacji na temat Kreatora projektów ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

## <a name="object_entry_auto"></a><a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO

Wprowadza obiekt ATL do mapy obiektu, aktualizuje rejestr i tworzy wystąpienie obiektu.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
[w] ClSID klasy COM zaimplementowane przez klasę C++ *o*nazwie .

*class*<br/>
[w] Nazwa klasy C++ implementująca klasę COM reprezentowaną przez *clsid*.

### <a name="remarks"></a>Uwagi

Makra wprowadzania obiektów są umieszczane w zakresie globalnym w projekcie, aby zapewnić obsługę rejestracji, inicjowania i tworzenia klasy.

OBJECT_ENTRY_AUTO wprowadza wskaźniki funkcji klasy twórcy i funkcji klasy fabrycznej dla `CreateInstance` tego obiektu do automatycznie generowanej mapy obiektów ATL. Gdy [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) jest wywoływana, aktualizuje rejestr systemowy dla każdego obiektu na mapie obiektu.

W poniższej tabeli opisano sposób otrzymywani informacji dodanych do mapy obiektu z klasy podanej jako drugi parametr tego makra.

|Informacje dla|Uzyskane z|
|---------------------|-------------------|
|Rejestracja COM|[Makra rejestru](../../atl/reference/registry-macros.md)|
|Tworzenie fabryki klas|[Makra fabryczne klasy](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Tworzenie wystąpienia|[Makra agregacji](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Rejestracja kategorii komponentów|[Makra kategorii](../../atl/reference/category-macros.md)|
|Inicjowanie i oczyszczanie na poziomie klasy|[ObiektMain](ccomobjectrootex-class.md#objectmain)|

## <a name="object_entry_non_createable_ex_auto"></a><a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Umożliwia określenie, że obiekt powinien zostać zarejestrowany i zainicjowany, ale nie `CoCreateInstance`powinien być można go tworzyć zewnętrznie za pośrednictwem obiektu .

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
[w] ClSID klasy COM zaimplementowane przez klasę C++ *o*nazwie .

*class*<br/>
[w] Nazwa klasy C++ implementująca klasę COM reprezentowaną przez *clsid*.

### <a name="remarks"></a>Uwagi

Makra wprowadzania obiektów są umieszczane w zakresie globalnym w projekcie, aby zapewnić obsługę rejestracji, inicjowania i tworzenia klasy.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO pozwala określić, że obiekt powinien zostać zarejestrowany i zainicjowany (zobacz [OBJECT_ENTRY_AUTO,](#object_entry_auto) aby uzyskać więcej `CoCreateInstance`informacji), ale nie należy go tworzyć za pomocą pliku .

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
