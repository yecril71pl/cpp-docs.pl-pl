---
title: Makra rejestru | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
dev_langs: C++
helpviewer_keywords: registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eada9ed75bd69122523350536d0757e98b31358d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="registry-macros"></a>Makra rejestru
Te makra zdefiniuj przydatne typu biblioteki i rejestru urządzenia.  
  
|||  
|-|-|  
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Wskazuje, że kod rejestracji dla obiekt w obiekt, aby uniknąć zależności ATL. BIBLIOTEKI DLL.|  
|[DECLARE_LIBID](#declare_libid)|Umożliwia ATL uzyskanie *identyfikatora libid* biblioteki typów.|  
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Pozwala uniknąć domyślne ATL rejestracji.|  
|[DECLARE_REGISTRY](#declare_registry)|Wprowadza lub usuwa obiekt główny wpis w rejestrze systemu.|  
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Określa informacje wymagane do automatycznego rejestrowania *appid*.|  
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Umożliwia znalezienie zasobów o nazwie i uruchamia skrypt rejestru w niej.|  
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Odnajduje zasobu określonego przez identyfikator, a następnie uruchamia skrypt rejestru w niej.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
    
##  <a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY  
 Symbol, który wskazuje, że kod rejestracji dla obiekt w obiekt, aby uniknąć zależności ATL. BIBLIOTEKI DLL.  
  
```
#define _ATL_STATIC_REGISTRY
```  
  
### <a name="remarks"></a>Uwagi  
 Podczas definiowania **ATL_STATIC_REGISTRY**, należy użyć poniższego kodu:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]  
  
##  <a name="declare_libid"></a>DECLARE_LIBID  
 Umożliwia ATL uzyskanie *identyfikatora libid* biblioteki typów.  
  
```
DECLARE_LIBID( libid )
```  
  
### <a name="parameters"></a>Parametry  
 *Identyfikator biblioteki*  
 Identyfikator GUID biblioteki typów.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `DECLARE_LIBID` w `CAtlModuleT`-klasy.  
  
### <a name="example"></a>Przykład  
 Atrybut inne niż projekty generowane przez kreatora ATL będzie miał próbkę przy użyciu tego makra.  
  
##  <a name="declare_no_registry"></a>DECLARE_NO_REGISTRY  
 Użyj `DECLARE_NO_REGISTRY` Jeśli chcesz uniknąć każdej rejestracji ATL domyślny dla klasy, w którym pojawi się to makro.  
  
```
DECLARE_NO_REGISTRY()
```  
  
##  <a name="declare_registry"></a>DECLARE_REGISTRY  
 Wejścia rejestracji klasa standardowa rejestru systemowego lub usuwa z rejestru systemowego.  
  
```
DECLARE_REGISTRY(
    class, 
    pid, 
    vpid, 
    nid, 
    flags )
```  
  
### <a name="parameters"></a>Parametry  
 `class`  
 [in] Zawarte dla zgodności z poprzednimi wersjami.  
  
 `pid`  
 [in] `LPCTSTR` Oznacza to identyfikator określonej wersji programu.  
  
 *vpid*  
 [in] `LPCTSTR` Czyli identyfikatora niezależną od wersji programu.  
  
 *nid*  
 [in] A **UINT** czyli indeksu ciągu zasobu w rejestrze ma być używana jako opis programu.  
  
 `flags`  
 [in] A `DWORD` zawierający program przez wątki modelu w rejestrze. Musi mieć jedną z następujących wartości: **THREADFLAGS_APARTMENT**, **THREADFLAGS_BOTH**, lub **AUTPRXFLAG**.  
  
### <a name="remarks"></a>Uwagi  
 Standardowa rejestracji składa się z identyfikatora CLSID, identyfikator programu, Identyfikatora niezależną od wersji programu, ciąg opisu i modelu wątku.  
  
 Podczas tworzenia obiektu lub kontrolować za pomocą Kreatora dodawania klasy ATL, Kreator automatycznie implementuje obsługę opartych na skryptach rejestru i dodaje [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) makro do plików. Jeśli nie chcesz, aby obsługa rejestru opartych na skryptach, musisz Zamień to makro z `DECLARE_REGISTRY`. `DECLARE_REGISTRY`Wstawia tylko pięć klucze podstawowe opisane powyżej w rejestrze. Ręcznie należy napisać kod, aby wstawić inne klucze do rejestru.  
  
##  <a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID  
 Określa informacje wymagane do automatycznego rejestrowania *appid*.  
  
```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid, 
    appid )
```  
  
### <a name="parameters"></a>Parametry  
 *resid*  
 Identyfikator zasobu w pliku .rgs, który zawiera informacje o *appid*.  
  
 *Identyfikator aplikacji*  
 IDENTYFIKATOR GUID.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `DECLARE_REGISTRY_APPID_RESOURCEID` w `CAtlModuleT`-klasy.  
  
### <a name="example"></a>Przykład  
 Klasy dodawane do projektów ATL za pomocą Kreatora dodawania klasy kod ma próbkę przy użyciu tego makra.  
  
##  <a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE  
 Pobiera zasób o nazwie zawierający plik rejestru i uruchamia skrypt wprowadź obiektów w rejestrze systemu lub usuń je z rejestru systemowego.  
  
```
DECLARE_REGISTRY_RESOURCE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Identyfikator zasobu ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Podczas tworzenia obiektu lub kontrolować za pomocą kreatora Projekt ATL, Kreator automatycznie wdrożyć techniczną opartych na skryptach rejestru i Dodaj [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) makra, która jest podobna do `DECLARE_REGISTRY_RESOURCE`, do użytkownika pliki.  
  
 Statycznie można połączyć z składnik rejestru Alt (Rejestrator) dla dostępu do rejestru zoptymalizowane. Statycznie łącza do kodu rejestratora, Dodaj następujący wiersz w pliku stdafx.h:  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Jeśli chcesz ATL do zastąpienia wartości zastępcze w czasie wykonywania, nie należy określać `DECLARE_REGISTRY_RESOURCE` lub `DECLARE_REGISTRY_RESOURCEID` makra. Zamiast tego Utwórz tablicę **_ATL_REGMAP_ENTRIES** struktur, w którym każdy wpis zawiera symbol zastępczy zmiennej łączyć się z wartości do Zastąp symbol zastępczy w czasie wykonywania. Następnie wywołaj [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) lub [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), przekazanie tablicy. Spowoduje to dodanie wszystkich wartości zastępcze w **_ATL_REGMAP_ENTRIES** struktury do mapy zastępczy rejestratora.  

  
 Aby uzyskać więcej informacji na temat parametrów wymiennych i skryptów, zobacz artykuł [składnik rejestru Alt (Rejestrator)](../../atl/atl-registry-component-registrar.md).  
  
##  <a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID  
 Taki sam jak [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) z tą różnicą, że używa wygenerowana przez kreatora **UINT** do identyfikacji zasobu, a nie nazwy ciągu.  
  
```
DECLARE_REGISTRY_RESOURCEID( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Generowane przez kreatora identyfikator zasobu.  
  
### <a name="remarks"></a>Uwagi  
 Podczas tworzenia obiektu lub kontrolować za pomocą kreatora Projekt ATL, Kreator automatycznie wdrożyć techniczną opartych na skryptach rejestru i Dodaj `DECLARE_REGISTRY_RESOURCEID` makro do plików.  
  
 Statycznie można połączyć z składnik rejestru Alt (Rejestrator) dla dostępu do rejestru zoptymalizowane. Statycznie łącza do kodu rejestratora, Dodaj następujący wiersz w pliku stdafx.h:  
  
 [!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Jeśli chcesz ATL do zastąpienia wartości zastępcze w czasie wykonywania, nie należy określać `DECLARE_REGISTRY_RESOURCE` lub `DECLARE_REGISTRY_RESOURCEID` makra. Zamiast tego Utwórz tablicę **_ATL_REGMAP_ENTRIES** struktur, w którym każdy wpis zawiera symbol zastępczy zmiennej łączyć się z wartości do Zastąp symbol zastępczy w czasie wykonywania. Następnie wywołaj [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) lub [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), przekazanie tablicy. Spowoduje to dodanie wszystkich wartości zastępcze w **_ATL_REGMAP_ENTRIES** struktury do mapy zastępczy rejestratora.  

  
 Aby uzyskać więcej informacji na temat parametrów wymiennych i skryptów, zobacz artykuł [składnik rejestru Alt (Rejestrator)](../../atl/atl-registry-component-registrar.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)
