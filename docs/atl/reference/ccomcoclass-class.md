---
title: Klasa klasy CComCoClass | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
dev_langs:
- C++
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 738d7e937acf2d3299be97b4f091c698582911d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365465"
---
# <a name="ccomcoclass-class"></a>Klasy CComCoClass — klasa
Ta klasa dostarcza metody do tworzenia wystąpień klasy i uzyskiwania jego właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, const CLSID* pclsid = &CLSID_NULL>  
class CComCoClass
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `CComCoClass`.  
  
 *pclsid*  
 Wskaźnik do identyfikatora CLSID obiektu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCoClass::CreateInstance](#createinstance)|(Statyczny) Tworzy wystąpienie klasy i zapytania dla interfejsu.|  
|[CComCoClass::Error](#error)|(Statyczny) Zwraca informacje o błędzie sformatowanego do klienta.|  
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|(Statyczny) Zwraca identyfikator klasy obiektu.|  
|[CComCoClass::GetObjectDescription](#getobjectdescription)|(Statyczny) Należy przesłonić, aby zwrócić opis obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CComCoClass` udostępnia metody pobierania identyfikatora CLSID obiektu, ustawiania informacji o błędach i tworzenia wystąpień klasy. Każda klasa zarejestrowane w [mapy obiektu](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f) powinien pochodzić z `CComCoClass`.  
  
 `CComCoClass` definiuje również domyślny klasy fabryki i agregację modelu dla obiektu. `CComCoClass` wykorzystuje dwa następujące makra:  
  
- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) deklaruje fabryki klasy jako [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).  
  
- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) deklaruje zagregowane obiektu.  
  
 Można zastąpić jedną z tych wartości domyślnych, określając innego makra w definicji klasy. Na przykład, aby użyć [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) zamiast `CComClassFactory`, określ [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) makra:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="createinstance"></a>  CComCoClass::CreateInstance  
 Użyj tych `CreateInstance` funkcji w celu utworzenia wystąpienia COM obiektu i pobrać wskaźnik interfejsu — bez przy użyciu interfejsu API modelu COM.  
  
```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `Q`  
 Interfejs COM, który ma zostać zwrócony przez `pp`.  
  
 *Parametr punkOuter*  
 [in] Zewnętrzne nieznany lub nieznany kontrolowanie agregacji.  
  
 `pp`  
 [out] Adres zmiennej wskaźnikowej odbierająca wskaźnika żądanego interfejsu, jeśli tworzenie zakończy się powodzeniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość. Zobacz [wywołanie funkcji CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615) w zestawie Windows SDK opis możliwych wartości zwracanych.  
  
### <a name="remarks"></a>Uwagi  
 Użyj pierwszego przeciążenia tej funkcji do utworzenia obiektu typowe; Użyj drugi przeciążenia, gdy potrzebne do agregacji tworzony obiekt.  
  
 Klasy ATL implementacji wymaganego obiektu modelu COM (to znaczy klasy używany jako pierwszy parametr szablonu w celu [klasy CComCoClass](../../atl/reference/ccomcoclass-class.md)) musi należeć do tego samego projektu jako kod wywołujący. Tworzenie obiektu modelu COM jest przeprowadzane przez fabrykę klas zarejestrowany dla tej klasy ATL.  
  
 Funkcje te są przydatne do tworzenia obiektów uniemożliwiających przed zewnętrznie możliwość utworzenia przy użyciu [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) makra. Są one również przydatne w sytuacjach, gdy chce się uniknąć interfejs API modelu COM, ze względu na wydajność.  
  
 Należy pamiętać, że interfejs `Q` musi mieć IID skojarzonych z nim, który można pobrać przy użyciu [__uuidof](../../cpp/uuidof-operator.md) operatora.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie `CDocument` jest klasą generowane przez kreatora ATL jest pochodną `CComCoClass` implementującej **IDocument** interfejsu. Klasa jest zarejestrowany w mapie obiektu z `OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO` makra, więc klienci nie można utworzyć wystąpienia w dokumencie przy użyciu [wywołanie funkcji CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615). `CApplication` jest klasą CoClass, który udostępnia metodę na jedną z jego własnej interfejsy modelu COM, można utworzyć wystąpienia klasy dokumentu. Kod poniżej przedstawia, jak łatwo go w celu utworzenia wystąpienia przy użyciu klasy dokumentu `CreateInstance` odziedziczony element członkowski `CComCoClass` klasy podstawowej.  
  
 [!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]  
  
##  <a name="error"></a>  CComCoClass::Error  
 Ta funkcja statyczna konfiguruje `IErrorInfo` interfejsu, aby podać informacje o błędzie do klienta.  
  
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
 `lpszDesc`  
 [in] Ciąg opisujący błąd. Wersja Unicode `Error` Określa, że `lpszDesc` jest typu **LPCOLESTR**; wersji ANSI Określa typ `LPCSTR`.  
  
 `iid`  
 [in] Uzyskanie identyfikatora IID interfejsu Definiowanie błąd lub `GUID_NULL` (wartość domyślna) Jeśli błąd został zdefiniowany przez system operacyjny.  
  
 `hRes`  
 [in] `HRESULT` Ma zwracany do obiektu wywołującego. Wartość domyślna to 0. Aby uzyskać więcej informacji o `hRes`, zobacz uwagi.  
  
 `nID`  
 [in] Identyfikator zasobu przechowywania ciąg opisu błędu. Ta wartość musi zawierać się między 0x0200 i 0xFFFF, włącznie. W kompilacjach do debugowania **ASSERT** spowoduje `nID` nie indeksowania prawidłowy ciąg. W kompilacjach wydania ciąg opisu błędu zostanie ustawiona na "Unknown Error".  
  
 `dwHelpID`  
 [in] Identyfikator kontekstu pomocy dla błędu.  
  
 `lpszHelpFile`  
 [in] Ścieżka i nazwa pliku pomocy opisem błędu.  
  
 `hInst`  
 [in] Dojście do zasobu. Domyślnie ten parametr jest **_AtlModule::GetResourceInstance**, gdzie **_AtlModule** jest globalne wystąpienie [CAtlModule](../../atl/reference/catlmodule-class.md).  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Aby wywołać `Error`, obiekt musi implementować `ISupportErrorInfo Interface` interfejsu.  
  
 Jeśli `hRes` parametru będzie różna od zera, `Error` zwraca wartość `hRes`. Jeśli `hRes` jest zero, a następnie pierwsze cztery wersje `Error` zwracać `DISP_E_EXCEPTION`. Ostatnie dwie wersje zwracają wynik makra **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)**.  
  
##  <a name="getobjectclsid"></a>  CComCoClass::GetObjectCLSID  
 Zapewnia spójny sposób pobierania identyfikatora CLSID obiektu.  
  
```
static const CLSID& WINAPI GetObjectCLSID();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator klasy obiektu.  
  
##  <a name="getobjectdescription"></a>  CComCoClass::GetObjectDescription  
 Ta funkcja statyczna pobiera tekst opisu dla obiekt klasy.  
  
```
static LPCTSTR WINAPI GetObjectDescription();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Opis obiektu klasy.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja zwraca **NULL**. Można zastąpić tej metody za pomocą [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description) makra. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]  
  
 `GetObjectDescription` Metoda jest wywoływana przez **IComponentRegistrar::GetComponents**. **IComponentRegistrar** jest interfejsem automatyzacji, która pozwala na rejestrowanie i wyrejestrowywanie pojedynczych składników w bibliotece DLL. Podczas tworzenia obiektu rejestratora składników przy użyciu kreatora Projekt ATL, Kreator automatycznie wykona **IComponentRegistrar** interfejsu. **IComponentRegistrar** jest zwykle używany przez program Microsoft Transaction Server.  
  
 Aby uzyskać więcej informacji o Kreatorze Projekt ATL, zobacz artykuł [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
