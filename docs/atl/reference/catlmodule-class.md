---
title: Klasa CAtlModule
ms.date: 11/04/2016
f1_keywords:
- CAtlModule
- ATLBASE/ATL::CAtlModule
- ATLBASE/ATL::CAtlModule::CAtlModule
- ATLBASE/ATL::CAtlModule::AddCommonRGSReplacements
- ATLBASE/ATL::CAtlModule::AddTermFunc
- ATLBASE/ATL::CAtlModule::GetGITPtr
- ATLBASE/ATL::CAtlModule::GetLockCount
- ATLBASE/ATL::CAtlModule::Lock
- ATLBASE/ATL::CAtlModule::Term
- ATLBASE/ATL::CAtlModule::Unlock
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceDHelper
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CAtlModule::m_libid
- ATLBASE/ATL::CAtlModule::m_pGIT
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
ms.openlocfilehash: 10658b118c97afe99144c3a4d25e0297aba3727f
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168018"
---
# <a name="catlmodule-class"></a>Klasa CAtlModule

Ta klasa udostępnia metody używane przez kilka klas modułów ATL.

## <a name="syntax"></a>Składnia

```cpp
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlModule::CAtlModule](#catlmodule)|Konstruktor.|
|[CAtlModule:: ~ CAtlModule](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|Zastąp tę metodę, aby dodać parametry do mapy wymiany składnika rejestru ATL (rejestratora).|
|[CAtlModule::AddTermFunc](#addtermfunc)|Dodaje nową funkcję, która ma być wywoływana po zakończeniu działania modułu.|
|[CAtlModule::GetGITPtr](#getgitptr)|Zwraca wskaźnik interfejsu globalnego.|
|[CAtlModule::GetLockCount](#getlockcount)|Zwraca liczbę blokad.|
|[CAtlModule:: Lock](#lock)|Zwiększa liczbę blokad.|
|[CAtlModule:: Term](#term)|Zwalnia wszystkie elementy członkowskie danych.|
|[CAtlModule:: Unlock](#unlock)|Zmniejsza liczbę blokad.|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt.|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Ta metoda jest wywoływana przez `UpdateRegistryFromResourceD` program w celu przeprowadzenia aktualizacji rejestru.|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt. Ta metoda statycznie łączy się ze składnikiem rejestru ATL.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlModule:: m_libid](#m_libid)|Zawiera identyfikator GUID bieżącego modułu.|
|[CAtlModule:: m_pGIT](#m_pgit)|Wskaźnik do tabeli interfejsu globalnego.|

## <a name="remarks"></a>Uwagi

Ta klasa jest używana przez klasy [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md), [klasy CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)i [Funkcja CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) w celu zapewnienia obsługi odpowiednio dla aplikacji DLL, aplikacji exe i usług systemu Windows.

Aby uzyskać więcej informacji na temat modułów w ATL, zobacz [klasy modułów ATL](../../atl/atl-module-classes.md).

Ta klasa zastępuje przestarzałą [klasę CComModule](../../atl/reference/ccommodule-class.md) używaną we wcześniejszych wersjach ATL.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="catlmoduleaddcommonrgsreplacements"></a><a name="addcommonrgsreplacements"></a>CAtlModule::AddCommonRGSReplacements

Zastąp tę metodę, aby dodać parametry do mapy wymiany składnika rejestru ATL (rejestratora).

```cpp
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>Parametry

*pRegistrar*<br/>
Zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Parametry wymienne umożliwiają klientowi rejestratora określanie danych czasu wykonywania. W tym celu Rejestrator utrzymuje mapę zastępującą, do której wprowadza wartości skojarzone z parametrami wymiennymi w skrypcie. Rejestrator wprowadza te wpisy w czasie wykonywania.

Aby uzyskać więcej informacji, zobacz temat [Używanie parametrów wymiennych (preprocesora rejestratora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) .

## <a name="catlmoduleaddtermfunc"></a><a name="addtermfunc"></a>CAtlModule::AddTermFunc

Dodaje nową funkcję, która ma być wywoływana po zakończeniu działania modułu.

```cpp
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>Parametry

*pFunc*<br/>
Wskaźnik do funkcji, która ma zostać dodana.

*magazynu*<br/>
Dane zdefiniowane przez użytkownika, przekazanie do funkcji.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

## <a name="catlmodulecatlmodule"></a><a name="catlmodule"></a>CAtlModule::CAtlModule

Konstruktor.

```cpp
CAtlModule() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje składowe danych i inicjuje sekcję krytyczną wokół wątku modułu.

## <a name="catlmodulecatlmodule"></a><a name="dtor"></a>CAtlModule:: ~ CAtlModule

Destruktor.

```cpp
~CAtlModule() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie elementy członkowskie danych.

## <a name="catlmodulegetgitptr"></a><a name="getgitptr"></a>CAtlModule::GetGITPtr

Pobiera wskaźnik do tabeli interfejsu globalnego.

```cpp
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>Parametry

*ppGIT*<br/>
Wskaźnik do zmiennej, która będzie odbierać wskaźnik do tabeli interfejsu globalnego.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK dla sukcesu lub kod błędu w przypadku niepowodzenia. E_POINTER jest zwracana, jeśli wartość *ppGIT* jest równa null.

### <a name="remarks"></a>Uwagi

Jeśli obiekt tabeli interfejsu globalnego nie istnieje, zostanie utworzony, a jego adres jest przechowywany w zmiennej składowej [CAtlModule:: m_pGIT](#m_pgit).

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *ppGIT* jest równa null, lub jeśli nie można uzyskać wskaźnika tabeli interfejsu globalnego.

Zobacz [IGlobalInterfaceTable](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable) , aby uzyskać informacje o globalnej tabeli interfejsów.

## <a name="catlmodulegetlockcount"></a><a name="getlockcount"></a>CAtlModule::GetLockCount

Zwraca liczbę blokad.

```cpp
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę blokad. Ta wartość może być przydatna w przypadku diagnostyki i debugowania.

## <a name="catlmodulelock"></a><a name="lock"></a>CAtlModule:: Lock

Zwiększa liczbę blokad.

```cpp
virtual LONG Lock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwiększa liczbę blokad i zwraca zaktualizowaną wartość. Ta wartość może być przydatna w przypadku diagnostyki i debugowania.

## <a name="catlmodulem_libid"></a><a name="m_libid"></a>CAtlModule:: m_libid

Zawiera identyfikator GUID bieżącego modułu.

```cpp
static GUID m_libid;
```

## <a name="catlmodulem_pgit"></a><a name="m_pgit"></a>CAtlModule:: m_pGIT

Wskaźnik do tabeli interfejsu globalnego.

```cpp
IGlobalInterfaceTable* m_pGIT;
```

## <a name="catlmoduleterm"></a><a name="term"></a>CAtlModule:: Term

Zwalnia wszystkie elementy członkowskie danych.

```cpp
void Term() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie elementy członkowskie danych. Ta metoda jest wywoływana przez destruktor.

## <a name="catlmoduleunlock"></a><a name="unlock"></a>CAtlModule:: Unlock

Zmniejsza liczbę blokad.

```cpp
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zmniejsza liczbę blokad i zwraca zaktualizowaną wartość. Ta wartość może być przydatna w przypadku diagnostyki i debugowania.

## <a name="catlmoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CAtlModule::UpdateRegistryFromResourceD

Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt.

```cpp
HRESULT WINAPI UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parametry

*lpszRes*<br/>
Nazwa zasobu.

*nResID*<br/>
Identyfikator zasobu.

*bRegister*<br/>
Ma wartość TRUE, jeśli obiekt powinien być zarejestrowany; W przeciwnym razie zwraca wartość FALSE.

*pMapEntries*<br/>
Wskaźnik do mapowanej mapy przechowującej wartości skojarzone z parametrami wymiennymi skryptu. ATL automatycznie używa elementu% MODULE%. Aby użyć dodatkowych parametrów do przemieszczenia, zobacz [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements). W przeciwnym razie użyj wartości domyślnej o wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Uruchamia skrypt zawarty w zasobie określony przez *lpszRes lub nResID*. Jeśli *bRegister* ma wartość true, ta metoda rejestruje obiekt w rejestrze systemowym; w przeciwnym razie usuwa obiekt z rejestru.

Aby statycznie łączyć się ze składnikiem rejestru ATL (Rejestrator), zobacz [CAtlModule:: UpdateRegistryFromResourceS](#updateregistryfromresources).

Ta metoda wywołuje [CAtlModule:: UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) i [IRegistrar:: ResourceUnregister](iregistrar-class.md#resourceunregister).

## <a name="catlmoduleupdateregistryfromresourcedhelper"></a><a name="updateregistryfromresourcedhelper"></a>CAtlModule::UpdateRegistryFromResourceDHelper

Ta metoda jest wywoływana przez `UpdateRegistryFromResourceD` program w celu przeprowadzenia aktualizacji rejestru.

```cpp
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parametry

*lpszRes*<br/>
Nazwa zasobu.

*bRegister*<br/>
Wskazuje, czy obiekt powinien być zarejestrowany.

*pMapEntries*<br/>
Wskaźnik do mapowanej mapy przechowującej wartości skojarzone z parametrami wymiennymi skryptu. ATL automatycznie używa elementu% MODULE%. Aby użyć dodatkowych parametrów do przemieszczenia, zobacz [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements). W przeciwnym razie użyj wartości domyślnej o wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda zapewnia implementację [CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced).

## <a name="catlmoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CAtlModule::UpdateRegistryFromResourceS

Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt. Ta metoda statycznie łączy się ze składnikiem rejestru ATL.

```cpp
HRESULT WINAPI UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parametry

*nResID*<br/>
Identyfikator zasobu.

*lpszRes*<br/>
Nazwa zasobu.

*bRegister*<br/>
Wskazuje, czy skrypt zasobów powinien być zarejestrowany.

*pMapEntries*<br/>
Wskaźnik do mapowanej mapy przechowującej wartości skojarzone z parametrami wymiennymi skryptu. ATL automatycznie używa elementu% MODULE%. Aby użyć dodatkowych parametrów do przemieszczenia, zobacz [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements). W przeciwnym razie użyj wartości domyślnej o wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Podobnie jak w przypadku [CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced) , z wyjątkiem `CAtlModule::UpdateRegistryFromResourceS` tworzenia statycznego łącza do składnika rejestru ATL (Rejestrator).

## <a name="see-also"></a>Zobacz także

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)<br/>
[Składnik rejestru (Rejestrator)](../../atl/atl-registry-component-registrar.md)
