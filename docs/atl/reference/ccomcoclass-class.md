---
title: Klasa CComCoClass | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 475a4f4d5f39f7fdfa569441fb2cb0fc72b745a0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677885"
---
# <a name="ccomcoclass-class"></a>Klasa CComCoClass
Ta klasa dostarcza metody do tworzenia wystąpienia klasy i uzyskania jej właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, const CLSID* pclsid = &CLSID_NULL>  
class CComCoClass
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `CComCoClass`.  
  
 *pclsid*  
 Wskaźnik do identyfikatora CLSID obiektu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCoClass::CreateInstance](#createinstance)|(Statyczny) Tworzy wystąpienie klasy i zapytania dla interfejsu.|  
|[CComCoClass::Error](#error)|(Statyczny) Zwraca szczegółowych informacji o błędach do klienta.|  
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|(Statyczny) Zwraca identyfikator klasy obiektów.|  
|[CComCoClass::GetObjectDescription](#getobjectdescription)|(Statyczny) Należy przesłonić, aby zwrócić opis obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CComCoClass` udostępnia metody do pobierania identyfikatora CLSID obiektu, ustawiania informacji o błędach i tworzenia wystąpienia klasy. Każda klasa zarejestrowany na mapie obiektu powinien pochodzić od `CComCoClass`.  
  
 `CComCoClass` definiuje również domyślne klasy fabryki i agregację modelu obiektu. `CComCoClass` wykorzystuje dwa następujące makra:  
  
- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) deklaruje fabryki klas jako [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).  
  
- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) deklaruje, że obiekt może być agregowany.  
  
 Można zastąpić jedną z tych wartości domyślnych, określając innego makra w definicji klasy. Na przykład, aby użyć [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) zamiast `CComClassFactory`, określ [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) makra:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="createinstance"></a>  CComCoClass::CreateInstance  
 Te `CreateInstance` functions w celu utworzenia wystąpienia COM object i pobrać wskaźnika interfejsu bez korzystania z interfejsu API modelu COM.  
  
```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```  
  
### <a name="parameters"></a>Parametry  
 *PYTANIA I ODPOWIEDZI*  
 Interfejs COM, który ma zostać zwrócone za pośrednictwem *pp*.  
  
 *punkOuter*  
 [in] Nieznany zewnętrznego lub kontrolowanie nieznane agregacji.  
  
 *strony*  
 [out] Adres zmiennej wskaźnika, który otrzymuje wskaźnik żądanego interfejsu, jeśli tworzenie zakończy się powodzeniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT. Zobacz [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance) w zestawie Windows SDK opis możliwych wartości zwracanych.  
  
### <a name="remarks"></a>Uwagi  
 Do utworzenia obiektu typowe; Użyj pierwsze przeciążenie tej funkcji drugie przeciążenie należy użyć, gdy należy zagregować tworzonego obiektu.  
  
 Klasy ATL implementacji wymaganego obiektu COM (oznacza to, klasy, które są używane jako pierwszy parametr szablonu [CComCoClass](../../atl/reference/ccomcoclass-class.md)) musi znajdować się w tym samym projekcie jako kod wywołujący. Tworzenie obiektu COM jest realizowane przez fabrykę klas zarejestrowany dla tej klasy ATL.  
  
 Te funkcje są przydatne do tworzenia obiektów, które należy mieć powstrzymywane przed zostaniem zewnętrznie utworzone za pomocą [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) makra. Są one również przydatne w sytuacjach, w którym chcesz uniknąć interfejs API modelu COM ze względów wydajności.  
  
 Należy pamiętać, że interfejs *Q* musi mieć skojarzone z nim IID, można pobrać przy użyciu [__uuidof](../../cpp/uuidof-operator.md) operatora.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie `CDocument` jest generowane przez kreatora ATL klasa jest pochodną `CComCoClass` implementującej `IDocument` interfejsu. Klasa jest rejestrowana na mapie obiektów za pomocą makra OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO, dzięki czemu klienci nie można utworzyć wystąpienia dokumentu przy użyciu [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance). `CApplication` jest klasą CoClass zapewniającą metodę na jedną z własną interfejsów COM, aby utworzyć wystąpienia klasy dokumentu. Poniższy kod przedstawia, jak łatwo go, aby utworzyć wystąpienia klasy dokumentu przy użyciu `CreateInstance` element członkowski jest dziedziczony z `CComCoClass` klasy bazowej.  
  
 [!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]  
  
##  <a name="error"></a>  CComCoClass::Error  
 Ta funkcja statyczna konfiguruje `IErrorInfo` interfejsu, aby zapewnić informacje o błędzie do klienta.  
  
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
 *lpszDesc*  
 [in] Ciąg opisujący błąd. Wersja Unicode `Error` Określa, że *lpszDesc* jest typ LPCOLESTR; wersji ANSI Określa typ LPCSTR.  
 *IID*  
 [in] Identyfikator IID interfejsu Definiowanie błąd lub GUID_NULL (wartość domyślna), jeśli ten błąd jest zdefiniowany przez system operacyjny.  
  
 *parametrem typu HRESULT*  
 [in] Wartość HRESULT, które mają zwracany do obiektu wywołującego. Wartość domyślna to 0. Aby uzyskać więcej informacji na temat *parametrem typu HRESULT*, zobacz uwagi.  
  
 *nID*  
 [in] Identyfikator zasobu, gdzie znajduje się ciąg opisu błędu. Ta wartość musi zawierać się między 0x0200 i 0xFFFF, włącznie. W kompilacjach do debugowania **ASERCJA** spowoduje, że jeśli *nID* indeksowania prawidłowy ciąg. W kompilacjach do wydania ciąg opisu błędu zostanie ustawiony na "Nieznany błąd."  
  
 *dwHelpID*  
 [in] Identyfikator kontekstu pomocy dla błędu.  
  
 *lpszHelpFile*  
 [in] Ścieżka i nazwa pliku pomocy, opisujący błąd.  
  
 *hInst*  
 [in] Dojście do zasobu. Domyślnie ten parametr jest `_AtlModule::GetResourceInstance`, gdzie `_AtlModule` jest globalne wystąpienie [CAtlModule](../../atl/reference/catlmodule-class.md).  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Aby wywołać `Error`, obiekt musi implementować `ISupportErrorInfo Interface` interfejsu.  
  
 Jeśli *parametrem typu HRESULT* parametru będzie różna od zera, `Error` zwraca wartość *parametrem typu HRESULT*. Jeśli *parametrem typu HRESULT* jest zero, a następnie pierwsze cztery wersje `Error` zwraca DISP_E_EXCEPTION. Ostatnie dwie wersje zwracają wynik makra **MAKE_HRESULT (1, FACILITY_ITF,** *nID* **)**.  
  
##  <a name="getobjectclsid"></a>  CComCoClass::GetObjectCLSID  
 Zapewnia spójny sposób pobierania identyfikatora CLSID obiektu.  
  
```
static const CLSID& WINAPI GetObjectCLSID();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator klasy obiektów.  
  
##  <a name="getobjectdescription"></a>  CComCoClass::GetObjectDescription  
 Ta funkcja statyczna pobiera tekst opisu dla obiektu klasy.  
  
```
static LPCTSTR WINAPI GetObjectDescription();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Opis obiektu klasy.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja zwraca wartość NULL. Mogą przesłaniać tę metodę, przy użyciu [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description) makra. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]  
  
 `GetObjectDescription` jest wywoływana przez `IComponentRegistrar::GetComponents`. `IComponentRegistrar` to interfejs automatyzacji, która umożliwia rejestrowanie i wyrejestrowywanie poszczególne składniki w bibliotece DLL. Po utworzeniu obiektu rejestratora składników za pomocą Kreatora projektu ATL, Kreator automatycznie wdroży `IComponentRegistrar` interfejsu. `IComponentRegistrar` zwykle jest używana przez program Microsoft Transaction Server.  
  
 Aby uzyskać więcej informacji na temat Kreator projektów ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
