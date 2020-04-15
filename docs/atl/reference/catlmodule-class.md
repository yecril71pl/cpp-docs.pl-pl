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
ms.openlocfilehash: 378c8634e00935c622f0bf5d06a4f6c50cc60cb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321422"
---
# <a name="catlmodule-class"></a>Klasa CAtlModule

Ta klasa zawiera metody używane przez kilka klas modułów ATL.

## <a name="syntax"></a>Składnia

```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlModule::CAtlModule](#catlmodule)|Konstruktor.|
|[CAtlModule::~CAtlModule](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements CAtlModule::AddCommonRGSReplacements CAtlModule::AddCommonRGSReplacements CA](#addcommonrgsreplacements)|Zastąpokaj tę metodę, aby dodać parametry do mapy zastępczej składnika rejestru ATL (Registrar).|
|[CAtlModule::AddTermFunc](#addtermfunc)|Dodaje nową funkcję, która ma zostać wywołana po zakończeniu modułu.|
|[CAtlModule::GetGITPtr](#getgitptr)|Zwraca wskaźnik interfejsu globalnego.|
|[CAtlModule::GetLockCount](#getlockcount)|Zwraca liczbę blokad.|
|[CAtlModule::Blokada](#lock)|Zwiększa liczbę blokad.|
|[CAtlModule::Termin](#term)|Zwalnia wszystkich elementów członkowskich danych.|
|[CAtlModule::Odblokuj](#unlock)|Zmniejsza liczbę blokad.|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt.|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Ta metoda jest `UpdateRegistryFromResourceD` wywoływana przez do wykonania aktualizacji rejestru.|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt. Ta metoda statycznie łączy się ze składnikiem rejestru ATL.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAtlModule::m_libid](#m_libid)|Zawiera identyfikator GUID bieżącego modułu.|
|[CAtlModule::m_pGIT](#m_pgit)|Wskaźnik do tabeli interfejsu globalnego.|

## <a name="remarks"></a>Uwagi

Ta klasa jest używana przez [CAtlDllModuleT Class](../../atl/reference/catldllmodulet-class.md), [CAtlExeModuleT Class](../../atl/reference/catlexemodulet-class.md)i [CAtlServiceModuleT Class](../../atl/reference/catlservicemodulet-class.md) do zapewnienia obsługi aplikacji DLL, aplikacji EXE i usług systemu Windows, odpowiednio.

Aby uzyskać więcej informacji na temat modułów w ATL, zobacz [klasy modułów ATL](../../atl/atl-module-classes.md).

Ta klasa zastępuje przestarzałe [CComModule Class](../../atl/reference/ccommodule-class.md) używane we wcześniejszych wersjach ATL.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="catlmoduleaddcommonrgsreplacements"></a><a name="addcommonrgsreplacements"></a>CAtlModule::AddCommonRGSReplacements CAtlModule::AddCommonRGSReplacements CAtlModule::AddCommonRGSReplacements CA

Zastąpokaj tę metodę, aby dodać parametry do mapy zastępczej składnika rejestru ATL (Registrar).

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>Parametry

*pRegistrar (rejestrator)*<br/>
Zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Wymienne parametry umożliwiają klientowi rejestratora określenie danych w czasie wykonywania. W tym celu rejestrator zachowuje mapę zastępczą, do której wprowadza wartości skojarzone z wymiennymi parametrami w skrypcie. Rejestrator wprowadza te wpisy w czasie wykonywania.

Więcej informacji można znaleźć w temacie [Korzystanie z parametrów wymiennych (preprocesor rejestratora).](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

## <a name="catlmoduleaddtermfunc"></a><a name="addtermfunc"></a>CAtlModule::AddTermFunc

Dodaje nową funkcję, która ma zostać wywołana po zakończeniu modułu.

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>Parametry

*pFunc (Niemowny)*<br/>
Wskaźnik do funkcji, aby dodać.

*Dw*<br/>
Dane zdefiniowane przez użytkownika, przekazywane do funkcji.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="catlmodulecatlmodule"></a><a name="catlmodule"></a>CAtlModule::CAtlModule

Konstruktor.

```
CAtlModule() throw();
```

### <a name="remarks"></a>Uwagi

Inicjuje elementy członkowskie danych i inicjuje sekcję krytyczną wokół wątku modułu.

## <a name="catlmodulecatlmodule"></a><a name="dtor"></a>CAtlModule::~CAtlModule

Destruktor.

```
~CAtlModule() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkich elementów członkowskich danych.

## <a name="catlmodulegetgitptr"></a><a name="getgitptr"></a>CAtlModule::GetGITPtr

Pobiera wskaźnik do tabeli interfejsu globalnego.

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>Parametry

*ppGIT (polski)*<br/>
Wskaźnik do zmiennej, która otrzyma wskaźnik do tabeli interfejsu globalnego.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub kod błędu w przypadku awarii. E_POINTER jest zwracany, jeśli *ppGIT* jest równa NULL.

### <a name="remarks"></a>Uwagi

Jeśli obiekt Tabela interfejsu globalnego nie istnieje, jest tworzony, a jego adres jest przechowywany w zmiennej członkowskiej [CAtlModule::m_pGIT](#m_pgit).

W kompilacjach debugowania wystąpi błąd potwierdzenia, jeśli *ppGIT* jest równa NULL lub jeśli nie można uzyskać wskaźnika tabeli interfejsu globalnego.

Zobacz [IGlobalInterfaceTable](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable) informacji na temat tabeli interfejsu globalnego.

## <a name="catlmodulegetlockcount"></a><a name="getlockcount"></a>CAtlModule::GetLockCount

Zwraca liczbę blokad.

```
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę blokad. Ta wartość może być przydatne do diagnostyki i debugowania.

## <a name="catlmodulelock"></a><a name="lock"></a>CAtlModule::Blokada

Zwiększa liczbę blokad.

```
virtual LONG Lock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwiększa liczbę blokad i zwraca zaktualizowaną wartość. Ta wartość może być przydatne do diagnostyki i debugowania.

## <a name="catlmodulem_libid"></a><a name="m_libid"></a>CAtlModule::m_libid

Zawiera identyfikator GUID bieżącego modułu.

```
static GUID m_libid;
```

## <a name="catlmodulem_pgit"></a><a name="m_pgit"></a>CAtlModule::m_pGIT

Wskaźnik do tabeli interfejsu globalnego.

```
IGlobalInterfaceTable* m_pGIT;
```

## <a name="catlmoduleterm"></a><a name="term"></a>CAtlModule::Termin

Zwalnia wszystkich elementów członkowskich danych.

```
void Term() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkich elementów członkowskich danych. Ta metoda jest wywoływana przez destruktora.

## <a name="catlmoduleunlock"></a><a name="unlock"></a>CAtlModule::Odblokuj

Zmniejsza liczbę blokad.

```
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zmniejsza liczbę blokad i zwraca zaktualizowaną wartość. Ta wartość może być przydatne do diagnostyki i debugowania.

## <a name="catlmoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CAtlModule::UpdateRegistryFromResourceD

Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt.

```
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

*nResID (700)*<br/>
Identyfikator zasobu.

*Bregister*<br/>
PRAWDA, jeśli obiekt powinien zostać zarejestrowany; FAŁSZ inaczej.

*pMapEntries (Nieskładka)*<br/>
Wskaźnik do mapy zastępczej przechowującej wartości skojarzone z wymiennymi parametrami skryptu. ATL automatycznie używa %MODULE%. Aby użyć dodatkowych parametrów wymiennych, zobacz [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). W przeciwnym razie należy użyć wartości domyślnej NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Uruchamia skrypt zawarty w zasobie określonym przez *lpszRes lub nResID*. Jeśli *bRegister* ma wartość TRUE, ta metoda rejestruje obiekt w rejestrze systemowym; w przeciwnym razie usuwa obiekt z rejestru.

Aby statycznie połączyć się ze składnikiem rejestru ATL (Rejestrator), zobacz [CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources).

Ta metoda wywołuje [CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) i [IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister).

## <a name="catlmoduleupdateregistryfromresourcedhelper"></a><a name="updateregistryfromresourcedhelper"></a>CAtlModule::UpdateRegistryFromResourceDHelper

Ta metoda jest `UpdateRegistryFromResourceD` wywoływana przez do wykonania aktualizacji rejestru.

```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parametry

*lpszRes*<br/>
Nazwa zasobu.

*Bregister*<br/>
Wskazuje, czy obiekt powinien zostać zarejestrowany.

*pMapEntries (Nieskładka)*<br/>
Wskaźnik do mapy zastępczej przechowującej wartości skojarzone z wymiennymi parametrami skryptu. ATL automatycznie używa %MODULE%. Aby użyć dodatkowych parametrów wymiennych, zobacz [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). W przeciwnym razie należy użyć wartości domyślnej NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta metoda zapewnia implementację [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced).

## <a name="catlmoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CAtlModule::UpdateRegistryFromResourceS

Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt. Ta metoda statycznie łączy się ze składnikiem rejestru ATL.

```
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

*nResID (700)*<br/>
Identyfikator zasobu.

*lpszRes*<br/>
Nazwa zasobu.

*Bregister*<br/>
Wskazuje, czy skrypt zasobu powinien być zarejestrowany.

*pMapEntries (Nieskładka)*<br/>
Wskaźnik do mapy zastępczej przechowującej wartości skojarzone z wymiennymi parametrami skryptu. ATL automatycznie używa %MODULE%. Aby użyć dodatkowych parametrów wymiennych, zobacz [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). W przeciwnym razie należy użyć wartości domyślnej NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Podobne do [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced) z wyjątkiem `CAtlModule::UpdateRegistryFromResourceS` tworzy statyczne łącze do składnika rejestru ATL (Rejestrator).

## <a name="see-also"></a>Zobacz też

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)<br/>
[Składnik rejestru (rejestrator)](../../atl/atl-registry-component-registrar.md)
