---
title: Makra rejestru | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0cf941171ef992c677c619a1c6a45ab9868526a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767959"
---
# <a name="registry-macros"></a>Makra rejestru

Te makra definiują przydatne typu biblioteki i rejestru urządzeń.

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Wskazuje, że kod rejestracji, aby obiekt mógł być w obiekcie, aby uniknąć zależności na ATL. BIBLIOTEKI DLL.|
|[DECLARE_LIBID](#declare_libid)|Zapewnia sposób ATL uzyskać *libid* biblioteki typów.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Pozwala uniknąć domyślne ATL rejestracji.|
|[DECLARE_REGISTRY](#declare_registry)|Wprowadza lub usuwa obiekt główny wpis w rejestrze systemowym.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Określa informacje wymagane do automatycznego rejestrowania *appid*.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Umożliwia znalezienie nazwany zasób, a następnie uruchamia skrypt rejestru znajdujący się w nim.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Umożliwia znalezienie zasobu określonego przez identyfikator, a następnie uruchamia skrypt rejestru znajdujący się w nim.|  

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="_atl_static_registry"></a>  _ATL_STATIC_REGISTRY

Symbol, który wskazuje, że chcesz, aby kod rejestracji, aby obiekt mógł być w obiekcie, aby uniknąć zależności na ATL. BIBLIOTEKI DLL.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Uwagi

Podczas definiowania ATL_STATIC_REGISTRY, należy użyć następującego kodu:

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

##  <a name="declare_libid"></a>  DECLARE_LIBID

Zapewnia sposób ATL uzyskać *libid* biblioteki typów.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Parametry

*Identyfikator biblioteki*  
Identyfikator GUID biblioteki typów.

### <a name="remarks"></a>Uwagi

Użyj DECLARE_LIBID w `CAtlModuleT`-klasy pochodnej.

### <a name="example"></a>Przykład

Przypisane inne niż generowane przez kreatora projektów ATL będzie miał Przykładowe użycie tego makra.

##  <a name="declare_no_registry"></a>  DECLARE_NO_REGISTRY

Jeśli chcesz uniknąć wszelkich rejestracji ATL domyślnego dla klasy, w którym pojawia się to makro, należy użyć DECLARE_NO_REGISTRY.

```
DECLARE_NO_REGISTRY()
```

##  <a name="declare_registry"></a>  DECLARE_REGISTRY

Wprowadza rejestracja standardowych klas w rejestrze systemowym lub usuwa je z rejestru systemowego.

```
DECLARE_REGISTRY(
    class, 
    pid, 
    vpid, 
    nid, 
    flags )
```

### <a name="parameters"></a>Parametry

*class*  
[in] Dostępny dla zgodności z poprzednimi wersjami.

*Identyfikator PID*  
[in] LPCTSTR, który jest identyfikatorem specyficzny dla wersji programu.

*vpid*  
[in] LPCTSTR, który jest identyfikatorem niezależny od wersji programu.

*nid*  
[in] UINT, indeksem ciągu zasobu w rejestrze, aby użyć jako opis programu.

*flagi*  
[in] DWORD zawierający programu modelu wątkowości w rejestrze. Musi mieć jedną z następujących wartości: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH lub AUTPRXFLAG.

### <a name="remarks"></a>Uwagi

Standardowa rejestracja składa się z identyfikatora CLSID, identyfikator programu, identyfikator niezależny od wersji programu, ciąg opisu i modelu wątku.

Podczas tworzenia obiektu lub sterować za pomocą Kreatora dodawania klasy ATL, Kreator automatycznie implementuje obsługę opartych na skryptach rejestru i dodaje [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) makr w plikach. Jeśli nie mają obsługi opartych na skryptach rejestru, musisz Zamień to makro DECLARE_REGISTRY. DECLARE_REGISTRY wstawia tylko pięć kluczy podstawowych opisane powyżej do rejestru. Należy ręcznie napisać kod do wstawienia innych kluczy do rejestru.

##  <a name="declare_registry_appid_resourceid"></a>  DECLARE_REGISTRY_APPID_RESOURCEID

Określa informacje wymagane do automatycznego rejestrowania *appid*.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid, 
    appid )
```

### <a name="parameters"></a>Parametry

*Atrybut resid*  
Identyfikator zasobu w pliku .rgs, który zawiera informacje o *appid*.

*Identyfikator aplikacji*  
IDENTYFIKATOR GUID.

### <a name="remarks"></a>Uwagi

Użyj DECLARE_REGISTRY_APPID_RESOURCEID w `CAtlModuleT`-klasy pochodnej.

### <a name="example"></a>Przykład

Klasy dodawane do projektów ATL za pomocą Kreatora dodawania klasy kod będzie Przykładowe użycie tego makra.

##  <a name="declare_registry_resource"></a>  DECLARE_REGISTRY_RESOURCE

Pobiera nazwany zasób zawierający plik rejestru, a następnie uruchamia skrypt w celu wprowadź obiektów w rejestrze systemu lub usuń je z rejestru systemowego.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Parametry

*x*  
[in] Identyfikator zasobu ciągu.

### <a name="remarks"></a>Uwagi

Podczas tworzenia obiektu lub sterować za pomocą Kreatora projektu ATL, Kreator automatycznie Implementowanie obsługi opartych na skryptach rejestru i Dodaj [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) makra, która jest podobna do DECLARE_REGISTRY_ ZASÓB do plików.

Możesz statycznie połączyć za pomocą składnik rejestru Alt (Rejestrator) dostęp do rejestru zoptymalizowane. Aby połączyć statycznie do kodu rejestratora, Dodaj następujący wiersz do pliku stdafx.h:

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Jeśli chcesz, aby ATL, aby zastąpić wartości zastępcze w czasie wykonywania, nie należy określać DECLARE_REGISTRY_RESOURCE lub DECLARE_REGISTRY_RESOURCEID makra. Zamiast tego utworzyć tablicę `_ATL_REGMAP_ENTRIES` struktur, w których każdy wpis zawiera symbol zastępczy zmiennej sparowane z wartością do Zastąp symbol zastępczy w czasie wykonywania. Następnie wywołaj [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) lub [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), przekazując tablicę. Spowoduje to dodanie wszystkich wartości zastępowania w `_ATL_REGMAP_ENTRIES` struktury do mapy zastąpienie rejestratora.  

Aby uzyskać więcej informacji na temat parametrów zastępowalnych i skryptów, zobacz artykuł [składnik rejestru Alt (Rejestrator)](../../atl/atl-registry-component-registrar.md).

##  <a name="declare_registry_resourceid"></a>  DECLARE_REGISTRY_RESOURCEID

Taki sam jak [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) z tą różnicą, że używa Unit generowane przez kreatora do identyfikacji zasobu, a nie nazwy ciągu.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Parametry

*x*  
[in] Generowane przez kreatora identyfikator zasobu.

### <a name="remarks"></a>Uwagi

Podczas tworzenia obiektu lub kontrolki przy użyciu Kreatora projektu ATL, Kreator automatycznie Implementowanie obsługi opartych na skryptach rejestru i Dodaj makro DECLARE_REGISTRY_RESOURCEID do plików.

Możesz statycznie połączyć za pomocą składnik rejestru Alt (Rejestrator) dostęp do rejestru zoptymalizowane. Aby połączyć statycznie do kodu rejestratora, Dodaj następujący wiersz do pliku stdafx.h:

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Jeśli chcesz, aby ATL, aby zastąpić wartości zastępcze w czasie wykonywania, nie należy określać DECLARE_REGISTRY_RESOURCE lub DECLARE_REGISTRY_RESOURCEID makra. Zamiast tego utworzyć tablicę `_ATL_REGMAP_ENTRIES` struktur, w których każdy wpis zawiera symbol zastępczy zmiennej sparowane z wartością do Zastąp symbol zastępczy w czasie wykonywania. Następnie wywołaj [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) lub [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), przekazując tablicę. Spowoduje to dodanie wszystkich wartości zastępowania w `_ATL_REGMAP_ENTRIES` struktury do mapy zastąpienie rejestratora.  

Aby uzyskać więcej informacji na temat parametrów zastępowalnych i skryptów, zobacz artykuł [składnik rejestru Alt (Rejestrator)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
