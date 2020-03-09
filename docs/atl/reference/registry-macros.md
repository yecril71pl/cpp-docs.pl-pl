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
ms.openlocfilehash: c2a70c15473798ba6eb2ef35e0b7ded395708586
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857154"
---
# <a name="registry-macros"></a>Makra rejestru

Te makra definiują użyteczne biblioteki typów i funkcje rejestru.

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Wskazuje, że kod rejestracyjny obiektu powinien znajdować się w obiekcie, aby uniknąć zależności w ATL. Bibliotece.|
|[DECLARE_LIBID](#declare_libid)|Zapewnia metodę ATL do uzyskania *identyfikatora LIBID* biblioteki typów.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Pozwala uniknąć domyślnej rejestracji ATL.|
|[DECLARE_REGISTRY](#declare_registry)|Wprowadza lub usuwa wpis obiektu głównego w rejestrze systemowym.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Określa informacje wymagane do automatycznego rejestrowania identyfikatora *AppID*.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Wyszukuje nazwany zasób i uruchamia w nim skrypt rejestru.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Znajduje zasób identyfikowany przez numer IDENTYFIKACYJNy i uruchamia w nim skrypt rejestru.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

Symbol wskazujący, że kod rejestracyjny obiektu powinien znajdować się w obiekcie, aby uniknąć zależności w ATL. Bibliotece.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Uwagi

Podczas definiowania ATL_STATIC_REGISTRY należy użyć następującego kodu:

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

##  <a name="declare_libid"></a>DECLARE_LIBID

Zapewnia metodę ATL do uzyskania *identyfikatora LIBID* biblioteki typów.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Parametry

*identyfikatora LIBID*<br/>
Identyfikator GUID biblioteki typów.

### <a name="remarks"></a>Uwagi

Użyj DECLARE_LIBID w klasie pochodnej `CAtlModuleT`.

### <a name="example"></a>Przykład

Nieprzypisane przez kreatora projekty ATL nie będą miały przykładu użycia tego makra.

##  <a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

Użyj DECLARE_NO_REGISTRY, jeśli chcesz uniknąć żadnej domyślnej rejestracji ATL dla klasy, w której pojawia się to makro.

```
DECLARE_NO_REGISTRY()
```

##  <a name="declare_registry"></a>DECLARE_REGISTRY

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
podczas Uwzględnione w celu zapewnienia zgodności z poprzednimi wersjami.

*identyfikatora*<br/>
podczas LPCTSTR, który jest identyfikatorem programu specyficznym dla wersji.

*vpid*<br/>
podczas LPCTSTR, który jest identyfikatorem programu niezależnym od wersji.

*nid*<br/>
podczas UINT, który jest indeksem ciągu zasobu w rejestrze do użycia jako opis programu.

*znaczników*<br/>
podczas Element DWORD zawierający model wątkowości programu w rejestrze. Musi mieć jedną z następujących wartości: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH lub AUTPRXFLAG.

### <a name="remarks"></a>Uwagi

Standardowa Rejestracja składa się z identyfikatora CLSID, identyfikatora programu, niezależnej od wersji programu, ciągu opisu i modelu wątku.

Podczas tworzenia obiektu lub kontrolki za pomocą Kreatora dodawania klas ATL Kreator automatycznie implementuje obsługę rejestru na podstawie skryptów i dodaje do plików makro [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) . Jeśli nie chcesz obsługiwać rejestru opartego na skrypcie, musisz zastąpić to makro DECLARE_REGISTRY. DECLARE_REGISTRY wstawia tylko pięć podstawowych kluczy opisanych powyżej do rejestru. Musisz ręcznie napisać kod, aby wstawić inne klucze do rejestru.

##  <a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

Określa informacje wymagane do automatycznego rejestrowania identyfikatora *AppID*.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>Parametry

*Resid*<br/>
Identyfikator zasobu pliku. RGS, który zawiera informacje o *identyfikatorze AppID*.

*AppID*<br/>
IDENTYFIKATOR GUID.

### <a name="remarks"></a>Uwagi

Użyj DECLARE_REGISTRY_APPID_RESOURCEID w klasie pochodnej `CAtlModuleT`.

### <a name="example"></a>Przykład

Klasy dodane do projektów ATL przy użyciu Kreatora dodawania kodu klasy będą miały przykład użycia tego makra.

##  <a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

Pobiera nazwany zasób zawierający plik rejestru i uruchamia skrypt w celu wprowadzenia obiektów do rejestru systemowego lub usunięcia ich z rejestru systemowego.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Parametry

*y*<br/>
podczas Identyfikator ciągu zasobu.

### <a name="remarks"></a>Uwagi

Podczas tworzenia obiektu lub kontrolki przy użyciu Kreatora projektu ATL Kreator automatycznie implementuje obsługę rejestru na podstawie skryptów i dodaje [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) makro, które jest podobne do DECLARE_REGISTRY_RESOURCE, do plików.

Aby zoptymalizować dostęp do rejestru, można statycznie łączyć się ze składnikiem rejestru ATL (rejestratorem). Aby statycznie łączyć się z kodem rejestratora, Dodaj następujący wiersz do pliku *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i jego starszych):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Jeśli chcesz, aby ATL zamieniał wartości zastępcze w czasie wykonywania, nie określaj DECLARE_REGISTRY_RESOURCE ani DECLARE_REGISTRY_RESOURCEID makra. Zamiast tego Utwórz tablicę struktur `_ATL_REGMAP_ENTRIES`, gdzie każdy wpis zawiera zmienną symbol zastępczy sparowany z wartością, aby zastąpić symbol zastępczy w czasie wykonywania. Następnie Wywołaj [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) lub [CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), przekazując tablicę. Spowoduje to dodanie wszystkich wartości zamiennych ze struktur `_ATL_REGMAP_ENTRIES` do mapy wymiany rejestratora.

Aby uzyskać więcej informacji na temat wymiennych parametrów i skryptów, zobacz artykuł dotyczący [składnika rejestru ATL (rejestratora)](../../atl/atl-registry-component-registrar.md).

##  <a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

Analogicznie jak [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) , z tą różnicą, że do identyfikowania zasobu jest używane użycie przez kreatora uint, a nie nazwy ciągu.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Parametry

*y*<br/>
podczas Identyfikator zasobu wygenerowany przez kreatora.

### <a name="remarks"></a>Uwagi

Podczas tworzenia obiektu lub kontrolki przy użyciu Kreatora projektu ATL Kreator automatycznie implementuje obsługę rejestru na podstawie skryptów i dodaje do plików makro DECLARE_REGISTRY_RESOURCEID.

Aby zoptymalizować dostęp do rejestru, można statycznie łączyć się ze składnikiem rejestru ATL (rejestratorem). Aby statycznie łączyć się z kodem rejestratora, Dodaj następujący wiersz do pliku *stdafx. h* (*PCH. h* w Visual Studio 2019 i nowszych):

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Jeśli chcesz, aby ATL zamieniał wartości zastępcze w czasie wykonywania, nie określaj DECLARE_REGISTRY_RESOURCE ani DECLARE_REGISTRY_RESOURCEID makra. Zamiast tego Utwórz tablicę struktur `_ATL_REGMAP_ENTRIES`, gdzie każdy wpis zawiera zmienną symbol zastępczy sparowany z wartością, aby zastąpić symbol zastępczy w czasie wykonywania. Następnie Wywołaj [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) lub [CAtlModule:: UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), przekazując tablicę. Spowoduje to dodanie wszystkich wartości zamiennych ze struktur `_ATL_REGMAP_ENTRIES` do mapy wymiany rejestratora.

Aby uzyskać więcej informacji na temat wymiennych parametrów i skryptów, zobacz artykuł dotyczący [składnika rejestru ATL (rejestratora)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Zobacz także

[Utworze](../../atl/reference/atl-macros.md)
