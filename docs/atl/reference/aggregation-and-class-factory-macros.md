---
title: Agregacja i makra fabryki klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_AGGREGATABLE
- atlcom/ATL::DECLARE_CLASSFACTORY
- atlcom/ATL::DECLARE_CLASSFACTORY_EX
- atlcom/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- atlcom/ATL::DECLARE_CLASSFACTORY_SINGLETON
- atlcom/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- atlcom/ATL::DECLARE_NOT_AGGREGATABLE
- atlcom/ATL::DECLARE_ONLY_AGGREGATABLE
- atlcom/ATL::DECLARE_POLY_AGGREGATABLE
- atlcom/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- atlcom/ATL::DECLARE_VIEW_STATUS
dev_langs:
- C++
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8569d4ecbbd74a6d2d37701a4ec22e56cbe9f100
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="aggregation-and-class-factory-macros"></a>Agregacja i makra fabryki klas
Makra te umożliwiają kontrolowanie agregacji i deklarowanie fabryki klas.  
  
|||  
|-|-|  
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Deklaruje, że obiekt może być agregowany (ustawienie domyślne).|  
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Deklaruje fabryki klasy jako [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), fabryki klasy ATL domyślne.|  
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Deklaruje obiekt fabryki klasy jako fabryki klasy.|  
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) jako fabryki klasy.|  
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabryki klasy.|  
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) jako fabryki klasy.|  
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Deklaruje wirtualnej `GetControllingUnknown` funkcji.|  
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Deklaruje, że obiekt nie może być agregowany.|  
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Deklaruje, że obiekt musi być agregowana.|  
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Sprawdza wartość zewnętrzne nieznany i deklaruje obiektu agregowaniu lub się agregowaniu, gdzie to właściwe.|  
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Ochrona obiektu zewnętrznego przed usunięciem podczas konstruowania obiektu wewnętrznego.|  
|[DECLARE_VIEW_STATUS](#declare_view_status)|Określa **podwójne** flagi do kontenera.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
   
##  <a name="declare_aggregatable"></a>  DECLARE_AGGREGATABLE  
 Określa, czy obiekt może agregować.  
  
```
DECLARE_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Nazwa klasy są definiowane jako się agregowaniu.  
  
### <a name="remarks"></a>Uwagi  
 [Klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera to makro, aby określić domyślny model agregacji. Aby zastąpić to ustawienie domyślne, określ [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) lub [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) makra w definicji klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="declare_classfactory"></a>  DECLARE_CLASSFACTORY  
 Deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako fabryki klasy.  
  
```
DECLARE_CLASSFACTORY()
```  
  
### <a name="remarks"></a>Uwagi  
 [Klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) używa to makro, aby zadeklarować domyślną fabrykę klas dla obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]  
  
##  <a name="ccomclassfactory_class"></a>  Klasa CComClassFactory  
 Ta klasa implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfejsu.  
  
```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>Uwagi  
 `CComClassFactory` implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfejsu, który zawiera metody do tworzenia obiektu określonego identyfikatora CLSID, a także blokowania fabryki klasy w pamięci, aby pozwolić na szybsze tworzenie nowych obiektów. **IClassFactory** musi zostać wdrożone dla każdej klasy, który zarejestrował w rejestrze systemu i do której można przypisać CLSID.  
  
 Zwykle obiektów ATL uzyskać fabryki klasy przez wynikających z [klasy CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](#declare_classfactory), który deklaruje `CComClassFactory` jako domyślną fabrykę klas. Aby zastąpić to ustawienie domyślne, określ jedną z `DECLARE_CLASSFACTORY` *XXX* makra w definicji klasy. Na przykład [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) makro używa określonej klasy fabryki klasy:  
  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
 Powyżej definicji klasy określa, że **CMyClassFactory** będzie używana jako fabryka klas domyślnego obiektu. **CMyClassFactory** musi pochodzić od `CComClassFactory` i zastąpić `CreateInstance`.  
  
 ATL udostępnia trzy makra, które deklaruje fabrykę klas:  
  
- [DECLARE_CLASSFACTORY2](#declare_classfactory2) używa [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), która kontroluje tworzenie za pośrednictwem licencji.  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) używa [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), która tworzy obiekty w wielu apartamentach.  
  
- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) używa [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), która tworzy pojedynczy [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) obiektu.  
  
##  <a name="declare_classfactory_ex"></a>  DECLARE_CLASSFACTORY_EX  
 Deklaruje `cf` być fabryki klasy.  
  
```
DECLARE_CLASSFACTORY_EX( cf )
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 [in] Nazwa klasy, która implementuje obiekt fabryki klasy.  
  
### <a name="remarks"></a>Uwagi  
 `cf` Parametru musi pochodzić od [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i zastąpić `CreateInstance` metody.  
  
 [Klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) obejmuje [DECLARE_CLASSFACTORY](#declare_classfactory) makra, która określa `CComClassFactory` jako domyślną fabrykę klas. Jednak przy tym `DECLARE_CLASSFACTORY_EX` makra w definicji klasy do obiektu, możesz zastąpić to ustawienie domyślne.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
##  <a name="declare_classfactory2"></a>  DECLARE_CLASSFACTORY2  
 Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) jako fabryki klasy.  
  
```
DECLARE_CLASSFACTORY2( lic )
```  
  
### <a name="parameters"></a>Parametry  
 *— Umowa licencyjna*  
 [in] Klasa, która implementuje `VerifyLicenseKey`, `GetLicenseKey`, i `IsLicenseValid`.  
  
### <a name="remarks"></a>Uwagi  
 [Klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) obejmuje [DECLARE_CLASSFACTORY](#declare_classfactory) makra, która określa [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Jednak przy tym `DECLARE_CLASSFACTORY2` makra w definicji klasy do obiektu, możesz zastąpić to ustawienie domyślne.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
##  <a name="ccomclassfactory2_class"></a>  Klasa CComClassFactory2  
 Ta klasa implementuje [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) interfejsu.  
  
```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```    
  
### <a name="parameters"></a>Parametry  
 *Licencji*  
 Klasa, która implementuje statycznej następujące funkcje:  
  
- **statyczne VerifyLicenseKey BOOL (BSTR** `bstr` **);**  
  
- **statyczne GetLicenseKey BOOL (DWORD** `dwReserved` **, BSTR\***  `pBstr` **);**  
  
- **statyczne BOOL IsLicenseValid ();**  
  
### <a name="remarks"></a>Uwagi  
 `CComClassFactory2` implementuje [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) interfejs, który jest rozszerzeniem z [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364). **IClassFactory2** formanty obiekt tworzenie za pośrednictwem licencji. Fabryki klas na maszynie licencjonowane wykonywania zapewniają klucz licencji środowiska wykonawczego. Ten klucz licencji umożliwia aplikacji do tworzenia wystąpień obiektów, gdy licencji pełne maszyny nie istnieje.  
  
 Zwykle obiektów ATL uzyskać fabryki klasy przez wynikających z [klasy CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](#declare_classfactory), który deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Aby użyć `CComClassFactory2`, określ [DECLARE_CLASSFACTORY2](#declare_classfactory2) makra w definicji klasy do obiektu. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
 **CMyLicense**, parametr szablonu w celu `CComClassFactory2`, musi implementować statyczne funkcje `VerifyLicenseKey`, `GetLicenseKey`, i `IsLicenseValid`. Poniżej przedstawiono przykład klasy proste licencji:  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]  
  
 `CComClassFactory2` pochodzi z obu **CComClassFactory2Base** i *licencji*. **CComClassFactory2Base**, z kolei jest pochodną **IClassFactory2** i **CComObjectRootEx\< CComGlobalsThreadModel >**.  
  
##  <a name="declare_classfactory_auto_thread"></a>  DECLARE_CLASSFACTORY_AUTO_THREAD  
 Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabryki klasy.  
  
```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```  
  
### <a name="remarks"></a>Uwagi  
 [Klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) obejmuje [DECLARE_CLASSFACTORY](#declare_classfactory) makra, która określa [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Jednak przy tym `DECLARE_CLASSFACTORY_AUTO_THREAD` makra w definicji klasy do obiektu, możesz zastąpić to ustawienie domyślne.  
  
 Podczas tworzenia obiektów w wielu apartamentach (na serwerze poza procesem), Dodaj `DECLARE_CLASSFACTORY_AUTO_THREAD` do swojej klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="ccomclassfactoryautothread_class"></a>  Klasa CComClassFactoryAutoThread  
 Ta klasa implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfejsu i umożliwia tworzenie w apartamentach wiele obiektów.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>Uwagi  
 `CComClassFactoryAutoThread` przypomina [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ale możliwe jest tworzenie w apartamentach wiele obiektów. Aby móc korzystać z tej pomocy technicznej, pochodzi z modułu EXE [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
 Zwykle obiektów ATL uzyskać fabryki klasy przez wynikających z [klasy CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](#declare_classfactory), który deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Aby użyć `CComClassFactoryAutoThread`, określ [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) makra w definicji klasy do obiektu. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="declare_classfactory_singleton"></a>  DECLARE_CLASSFACTORY_SINGLETON  
 Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) jako fabryki klasy.  
  
```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```  
  
### <a name="parameters"></a>Parametry  
 `obj`  
 [in] Nazwa klasy obiektu.  
  
### <a name="remarks"></a>Uwagi  
 [Klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) obejmuje [DECLARE_CLASSFACTORY](#declare_classfactory) makra, która określa [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Jednak przy tym `DECLARE_CLASSFACTORY_SINGLETON` makra w definicji klasy do obiektu, możesz zastąpić to ustawienie domyślne.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="ccomclassfactorysingleton_class"></a>  Klasa CComClassFactorySingleton  
 Ta klasa pochodzi od [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Klasy.  
  
 `CComClassFactorySingleton` pochodną [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu. Każde wywołanie `CreateInstance` metoda po prostu wysyła zapytanie do tego obiektu dla wskaźnika interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Zwykle obiektów ATL uzyskać fabryki klasy przez wynikających z [klasy CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](#declare_classfactory), który deklaruje `CComClassFactory` jako domyślną fabrykę klas. Aby użyć `CComClassFactorySingleton`, określ [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) makra w definicji klasy do obiektu. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="declare_get_controlling_unknown"></a>  DECLARE_GET_CONTROLLING_UNKNOWN  
 Deklaruje funkcję wirtualną `GetControllingUnknown`.  
  
```
DECLARE_GET_CONTROLLING_UNKNOWN()
```  
  
### <a name="remarks"></a>Uwagi  
 Dodaj makro do obiektu, jeśli otrzymasz komunikat o błędzie kompilatora `GetControllingUnknown` zdefiniowano (na przykład w **CComAggregateCreator**).  
  
##  <a name="declare_not_aggregatable"></a>  DECLARE_NOT_AGGREGATABLE  
 Określa, że obiekt nie może być agregowany.  
  
```
DECLARE_NOT_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Nazwa obiektu klasy są definiowane jako się agregowaniu.  
  
### <a name="remarks"></a>Uwagi  
 `DECLARE_NOT_AGGREGATABLE` powoduje, że `CreateInstance` do zwrócenia błędu ( **CLASS_E_NOAGGREGATION**) jeśli podejmowana jest próba do zagregowania na obiekt.  
  
 Domyślnie [klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera [DECLARE_AGGREGATABLE](#declare_aggregatable) makra, która określa, czy obiekt może agregować. Aby zmienić to zachowanie domyślne, Uwzględnij `DECLARE_NOT_AGGREGATABLE` w definicji klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="declare_only_aggregatable"></a>  DECLARE_ONLY_AGGREGATABLE  
 Określa, czy obiekt musi być agregowana.  
  
```
DECLARE_ONLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Nazwa obiektu klasy są definiowane jako tylko się agregowaniu.  
  
### <a name="remarks"></a>Uwagi  
 `DECLARE_ONLY_AGGREGATABLE` powoduje, że wystąpił błąd ( **E_FAIL**) jeśli podejmowana jest próba **CoCreate** obiektu jako obiektu nieagregowane.  
  
 Domyślnie [klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera [DECLARE_AGGREGATABLE](#declare_aggregatable) makra, która określa, czy obiekt może agregować. Aby zmienić to zachowanie domyślne, Uwzględnij `DECLARE_ONLY_AGGREGATABLE` w definicji klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]  
  
##  <a name="declare_poly_aggregatable"></a>  DECLARE_POLY_AGGREGATABLE  
 Określa, że wystąpienie **CComPolyObject \<**  *x* **>** jest tworzony podczas tworzenia obiektu.  
  
```
DECLARE_POLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>Parametry  
 *x*  
 [in] Nazwa obiektu klasy są definiowane jako agregowaniu lub się agregowaniu.  
  
### <a name="remarks"></a>Uwagi  
 Podczas tworzenia zaznaczono wartość zewnętrzne nieznany. Jeśli jest **NULL**, **IUnknown** jest zaimplementowany dla obiekt nieagregowane. Jeśli nie jest zewnętrzna nieznany **NULL**, **IUnknown** jest zaimplementowany dla obiekt zagregowanych.  
  
 Zaletą używania `DECLARE_POLY_AGGREGATABLE` jest uniknąć oba mających `CComAggObject` i `CComObject` w module obsługi zagregowane i nieagregowane przypadkach. Pojedynczy `CComPolyObject` obiektu obsługuje w obu przypadkach. Oznacza to, że tylko jedna kopia vtable i jedną kopię funkcji istnieje w module. Jeśli Twoje vtable jest duży, to znacznie zmniejszyć rozmiar modułu użytkownika. Jednak jeśli Twoje vtable jest mały, za pomocą `CComPolyObject` może spowodować nieco większy rozmiar modułu, ponieważ nie jest zoptymalizowana dla obiekt zagregowane lub nieagregowane są `CComAggObject` i `CComObject`.  
  
 `DECLARE_POLY_AGGREGATABLE` Makro automatycznie jest zadeklarowana w obiektu, jeśli Kreator formantu ATL umożliwia tworzenie Pełna kontrola.  
  
##  <a name="declare_protect_final_construct"></a>  DECLARE_PROTECT_FINAL_CONSTRUCT  

 Chroni przed usunięciem, jeśli obiekt (podczas [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) wewnętrznego obiektu zagregowane zwiększa liczbę odwołań, a następnie zmniejsza liczbę 0.  
  
```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```  
  
##  <a name="declare_view_status"></a>  DECLARE_VIEW_STATUS  
 Umieść w formantu ATL ActiveX klasy formantu, aby określić to makro **podwójne** flagi do kontenera.  
  
```
DECLARE_VIEW_STATUS( statusFlags )
```  
  
### <a name="parameters"></a>Parametry  
 `statusFlags`  
 [in] **Podwójne** flagi. Zobacz [podwójne](http://msdn.microsoft.com/library/windows/desktop/ms687201) listę flag.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)
