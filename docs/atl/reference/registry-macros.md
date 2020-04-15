---
title: Makra rejestru
ms.date: 08/19/2019
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
ms.openlocfilehash: fd012b4300f4cd72cdc9ab363b770ac1dbefa06e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326042"
---
# <a name="registry-macros"></a>Makra rejestru

Te makra definiują przydatne biblioteki typów i obiektów rejestru.

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Wskazuje, że chcesz, aby kod rejestracyjny obiektu był w obiekcie, aby uniknąć zależności od ATL. Dll.|
|[DECLARE_LIBID](#declare_libid)|Umożliwia atl, aby uzyskać *libid* biblioteki typów.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Pozwala uniknąć domyślnej rejestracji ATL.|
|[DECLARE_REGISTRY](#declare_registry)|Wprowadza lub usuwa wpis obiektu głównego w rejestrze systemowym.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Określa informacje wymagane do automatycznego zarejestrowania *appid*.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Znajduje nazwany zasób i uruchamia skrypt rejestru w nim.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Znajduje zasób identyfikowany przez numer identyfikacyjny i uruchamia skrypt rejestru w nim.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="_atl_static_registry"></a><a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

Symbol, który wskazuje, że chcesz, aby kod rejestracyjny obiektu znajduje się w obiekcie, aby uniknąć zależności od ATL. Dll.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Uwagi

Podczas definiowania ATL_STATIC_REGISTRY należy użyć następującego kodu:

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

## <a name="declare_libid"></a><a name="declare_libid"></a>DECLARE_LIBID

Umożliwia atl, aby uzyskać *libid* biblioteki typów.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Parametry

*libid*<br/>
Identyfikator GUID biblioteki typów.

### <a name="remarks"></a>Uwagi

Użyj DECLARE_LIBID w klasie `CAtlModuleT`pochodnej.

### <a name="example"></a>Przykład

Niepodające projektów ATL wygenerowanych przez kreatora będzie miało próbkę użycia tego makra.

## <a name="declare_no_registry"></a><a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

Użyj DECLARE_NO_REGISTRY, jeśli chcesz uniknąć domyślnej rejestracji ATL dla klasy, w której pojawia się to makro.

```
DECLARE_NO_REGISTRY()
```

## <a name="declare_registry"></a><a name="declare_registry"></a>DECLARE_REGISTRY

Wprowadza rejestrację klasy standardowej do rejestru systemowego lub usuwa ją z rejestru systemowego.

```
DECLARE_REGISTRY(
    class,
    pid,
    vpid,
    nid,
    flags )
```

### <a name="parameters"></a>Parametry

*class*<br/>
[w] Dołączone do zgodności z powrotem.

*Pid*<br/>
[w] LPCTSTR, który jest identyfikatorem programu specyficzne dla wersji.

*vpid (*<br/>
[w] LPCTSTR, który jest identyfikatorem programu niezależnego od wersji.

*Nid*<br/>
[w] UINT, który jest indeksem ciągu zasobu w rejestrze do użycia jako opis programu.

*flagi*<br/>
[w] Dword zawierający model wątków programu w rejestrze. Musi być jedną z następujących wartości: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH lub AUTPRXFLAG.

### <a name="remarks"></a>Uwagi

Standardowa rejestracja składa się z identyfikatora CLSID, identyfikatora programu, identyfikatora programu niezależnego od wersji, ciągu opisu i modelu wątku.

Podczas tworzenia obiektu lub formantu za pomocą Kreatora dodawania klasy ATL kreator automatycznie implementuje obsługę rejestru opartego na skryptach i dodaje do plików [makro DECLARE_REGISTRY_RESOURCEID.](#declare_registry_resourceid) Jeśli nie chcesz obsługi rejestru opartego na skryptach, musisz zastąpić to makro DECLARE_REGISTRY. DECLARE_REGISTRY wstawia tylko pięć podstawowych kluczy opisanych powyżej do rejestru. Aby wstawić inne klucze do rejestru, należy ręcznie napisać kod.

## <a name="declare_registry_appid_resourceid"></a><a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

Określa informacje wymagane do automatycznego zarejestrowania *appid*.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>Parametry

*Resid*<br/>
Identyfikator zasobu pliku rgs zawierającego informacje o *pliku appid*.

*Appid*<br/>
Identyfikator GUID.

### <a name="remarks"></a>Uwagi

Użyj DECLARE_REGISTRY_APPID_RESOURCEID w klasie `CAtlModuleT`pochodnej.

### <a name="example"></a>Przykład

Klasy dodane do projektów ATL za pomocą kreatora Dodaj kod klasy będą miały próbkę użycia tego makra.

## <a name="declare_registry_resource"></a><a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

Pobiera nazwany zasób zawierający plik rejestru i uruchamia skrypt, aby wprowadzić obiekty do rejestru systemowego lub usunąć je z rejestru systemowego.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Identyfikator ciągu zasobu.

### <a name="remarks"></a>Uwagi

Podczas tworzenia obiektu lub formantu za pomocą Kreatora projektów ATL kreator automatycznie zaimplementuje obsługę rejestru opartego na skryptach i doda do plików [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) makra, które jest podobne do DECLARE_REGISTRY_RESOURCE.

Można statycznie połączyć ze składnikiem rejestru ATL (Rejestrator) w celu uzyskania zoptymalizowanego dostępu do rejestru. Aby statycznie połączyć się z kodem rejestratora, dodaj następujący wiersz do pliku *pch.h* (*stdafx.h* w programie Visual Studio 2017 i wcześniejszych):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Jeśli chcesz, aby atl zastępować wartości zastępcze w czasie wykonywania, nie należy określać DECLARE_REGISTRY_RESOURCE lub DECLARE_REGISTRY_RESOURCEID makra. Zamiast tego należy utworzyć `_ATL_REGMAP_ENTRIES` tablicę struktur, w której każdy wpis zawiera zmienny symbol zastępczy sparowany z wartością zastępującą symbol zastępczy w czasie wykonywania. Następnie [wywołanie CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) lub [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), przekazywanie tablicy. Spowoduje to dodanie wszystkich wartości `_ATL_REGMAP_ENTRIES` zastępczych w strukturach do mapy zastępczej rejestratora.

Aby uzyskać więcej informacji na temat wymiennych parametrów i skryptów, zobacz artykuł [Składnik rejestru ATL (Rejestrator)](../../atl/atl-registry-component-registrar.md).

## <a name="declare_registry_resourceid"></a><a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

Tak samo jak [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) z tą różnicą, że używa generowanego przez kreatora UINT do identyfikowania zasobu, a nie nazwy ciągu.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Wygenerowany przez kreatora identyfikator zasobu.

### <a name="remarks"></a>Uwagi

Podczas tworzenia obiektu lub formantu za pomocą Kreatora projektów ATL kreator automatycznie zaimplementuje obsługę rejestru opartego na skryptach i doda makro DECLARE_REGISTRY_RESOURCEID do plików.

Można statycznie połączyć ze składnikiem rejestru ATL (Rejestrator) w celu uzyskania zoptymalizowanego dostępu do rejestru. Aby statycznie połączyć się z kodem rejestratora, dodaj następujący wiersz do pliku *stdafx.h* (*pch.h* w programie Visual Studio 2019 i nowszych):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Jeśli chcesz, aby atl zastępować wartości zastępcze w czasie wykonywania, nie należy określać DECLARE_REGISTRY_RESOURCE lub DECLARE_REGISTRY_RESOURCEID makra. Zamiast tego należy utworzyć `_ATL_REGMAP_ENTRIES` tablicę struktur, w której każdy wpis zawiera zmienny symbol zastępczy sparowany z wartością zastępującą symbol zastępczy w czasie wykonywania. Następnie [wywołanie CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) lub [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), przekazywanie tablicy. Spowoduje to dodanie wszystkich wartości `_ATL_REGMAP_ENTRIES` zastępczych w strukturach do mapy zastępczej rejestratora.

Aby uzyskać więcej informacji na temat wymiennych parametrów i skryptów, zobacz artykuł [Składnik rejestru ATL (Rejestrator)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
