---
title: Klasa CComCoClass
ms.date: 11/04/2016
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
ms.openlocfilehash: 11e724a982f3a2f404473dbdd34d848842cc8e14
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320812"
---
# <a name="ccomcoclass-class"></a>Klasa CComCoClass

Ta klasa zawiera metody tworzenia wystąpień klasy i uzyskiwania jej właściwości.

## <a name="syntax"></a>Składnia

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `CComCoClass`.

*sztlsid*<br/>
Wskaźnik do identyfikatora CLSID obiektu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComCoClass::Utwórz instance](#createinstance)|(Statyczne) Tworzy wystąpienie klasy i kwerend dla interfejsu.|
|[CComCoClass::Błąd](#error)|(Statyczne) Zwraca klientowi bogate informacje o błędzie.|
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|(Statyczne) Zwraca identyfikator klasy obiektu.|
|[CComCoClass::GetObjectDescription](#getobjectdescription)|(Statyczne) Zastąp, aby zwrócić opis obiektu.|

## <a name="remarks"></a>Uwagi

`CComCoClass`udostępnia metody pobierania identyfikatora CLSID obiektu, ustawiania informacji o błędzie i tworzenia wystąpień klasy. Każda klasa zarejestrowana na mapie obiektu `CComCoClass`powinna pochodzić z .

`CComCoClass`definiuje również domyślny model fabryczny klasy i agregacji dla obiektu. `CComCoClass`wykorzystuje następujące dwa makra:

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) Deklaruje fabrykę klas jako [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) Deklaruje, że obiekt może być agregowane.

Można zastąpić jedną z tych wartości domyślnych, określając inne makro w definicji klasy. Na przykład, aby użyć [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) zamiast `CComClassFactory`, określ [makro DECLARE_CLASSFACTORY2:](aggregation-and-class-factory-macros.md#declare_classfactory2)

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomcoclasscreateinstance"></a><a name="createinstance"></a>CComCoClass::Utwórz instance

Te `CreateInstance` funkcje można użyć do utworzenia wystąpienia obiektu COM i pobrania wskaźnika interfejsu bez użycia interfejsu API COM.

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>Parametry

*P*<br/>
Interfejs COM, który powinien zostać zwrócony za pośrednictwem *pp*.

*punkOuter (polski)*<br/>
[w] Zewnętrzna nieznana lub kontrolująca nieznana kruszywo.

*S*<br/>
[na zewnątrz] Adres zmiennej wskaźnika, która odbiera żądany wskaźnik interfejsu, jeśli utworzenie zakończy się pomyślnie.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT. Zobacz [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) w windows SDK opis możliwych wartości zwracanych.

### <a name="remarks"></a>Uwagi

Użyj pierwszego przeciążenia tej funkcji do tworzenia typowych obiektów; użyj drugiego przeciążenia, gdy trzeba agregować tworzony obiekt.

Klasa ATL implementująca wymagany obiekt COM (czyli klasa używana jako pierwszy parametr szablonu do [CComCoClass)](../../atl/reference/ccomcoclass-class.md)musi znajdować się w tym samym projekcie co kod wywołujący. Tworzenie obiektu COM jest przeprowadzane przez fabrykę klas zarejestrowaną dla tej klasy ATL.

Te funkcje są przydatne do tworzenia obiektów, które nie mogą być tworzyć zewnętrznie przy użyciu [makra OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO.](object-map-macros.md#object_entry_non_createable_ex_auto) Są one również przydatne w sytuacjach, w których chcesz uniknąć interfejsu API COM ze względu na wydajność.

Należy zauważyć, że interfejs *Q* musi mieć identyfikator skojarzony z nim, które mogą być pobierane za pomocą [operatora __uuidof.](../../cpp/uuidof-operator.md)

### <a name="example"></a>Przykład

W poniższym `CDocument` przykładzie jest wygenerowaną przez kreatora klasą `IDocument` ATL wywodzącą się z `CComCoClass` interfejsu. Klasa jest zarejestrowana na mapie obiektu z makrą OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO, dzięki czemu klienci nie mogą tworzyć wystąpień dokumentu przy użyciu [funkcji CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance). `CApplication`jest CoClass, który udostępnia metodę na jednym z własnych interfejsów COM do tworzenia wystąpień klasy dokumentu. Poniższy kod pokazuje, jak łatwo utworzyć wystąpienia klasy `CreateInstance` dokumentu przy `CComCoClass` użyciu elementu członkowskiego odziedziczonego po klasie podstawowej.

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

## <a name="ccomcoclasserror"></a><a name="error"></a>CComCoClass::Błąd

Ta funkcja statyczna `IErrorInfo` konfiguruje interfejs, aby zapewnić klientowi informacje o błędzie.

```
static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance ());

static HRESULT Error(
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>Parametry

*lpszDesc*<br/>
[w] Ciąg opisujący błąd. Wersja Unicode `Error` określa, że *lpszDesc* jest typu LPCOLESTR; wersja ANSI określa typ LPCSTR.

*Iid*<br/>
[w] Identyfikator interfejsu definiującego błąd lub GUID_NULL (wartość domyślna), jeśli błąd jest zdefiniowany przez system operacyjny.

*Hres*<br/>
[w] HRESULT, który ma powrócić do wywołującego. Wartość domyślna to 0. Aby uzyskać więcej informacji na temat *hRes*, zobacz Uwagi.

*Nid*<br/>
[w] Identyfikator zasobu, w którym jest przechowywany ciąg opisu błędu. Wartość ta powinna należeć do 0x0200 i 0xFFFF, włącznie. W kompilacjach debugowania **assert** spowoduje, jeśli *nID* nie indeksuje prawidłowego ciągu. W kompilacjach wersji ciąg opisu błędu zostanie ustawiony na "Nieznany błąd".

*dwHelpID (Pomoc EKwi.*<br/>
[w] Identyfikator kontekstu pomocy dla błędu.

*lpszHelpFile*<br/>
[w] Ścieżka i nazwa pliku pomocy opisującego błąd.

*hInst (WZT)*<br/>
[w] Dojście do zasobu. Domyślnie ten parametr `_AtlModule::GetResourceInstance`to `_AtlModule` , gdzie jest globalne wystąpienie [CAtlModule](../../atl/reference/catlmodule-class.md).

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT. Aby uzyskać szczegółowe informacje, zobacz Uwagi.

### <a name="remarks"></a>Uwagi

Aby `Error`wywołać, obiekt `ISupportErrorInfo Interface` musi implementować interfejs.

Jeśli parametr *hRes* nie ma `Error` wartościzerowej, zwraca wartość *hRes*. Jeśli *hRes* wynosi zero, pierwsze `Error` cztery wersje zwracane DISP_E_EXCEPTION. Dwie ostatnie wersje zwracają wynik **MAKE_HRESULT makra( 1, FACILITY_ITF,** *nID* **).**

## <a name="ccomcoclassgetobjectclsid"></a><a name="getobjectclsid"></a>CComCoClass::GetObjectCLSID

Zapewnia spójny sposób pobierania identyfikatora CLSID obiektu.

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator klasy obiektu.

## <a name="ccomcoclassgetobjectdescription"></a><a name="getobjectdescription"></a>CComCoClass::GetObjectDescription

Ta funkcja statyczna pobiera opis tekstowy obiektu klasy.

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>Wartość zwracana

Opis obiektu klasy.

### <a name="remarks"></a>Uwagi

Domyślna implementacja zwraca wartość NULL. Tę metodę można zastąpić [makro DECLARE_OBJECT_DESCRIPTION.](object-map-macros.md#declare_object_description) Przykład:

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription`jest wywoływana przez `IComponentRegistrar::GetComponents`. `IComponentRegistrar`to interfejs automatyzacji, który umożliwia rejestrowanie i wyrejestrowywać poszczególne składniki w biblioteki DLL. Podczas tworzenia obiektu rejestratora składników za pomocą Kreatora projektów ATL kreator `IComponentRegistrar` automatycznie zaimplementuje interfejs. `IComponentRegistrar`jest zwykle używany przez serwer transakcji firmy Microsoft.

Aby uzyskać więcej informacji na temat Kreatora projektów ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
