---
title: Agregacji i makra fabryki klas
ms.date: 11/04/2016
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
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: c0e3b6903e382ad56be9500792bec895a7641f00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497193"
---
# <a name="aggregation-and-class-factory-macros"></a>Agregacji i makra fabryki klas

Te makra umożliwiają kontrolowanie agregacji i fabryki klas deklarowanie.

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Deklaruje, że obiekt może być agregowana (ustawienie domyślne).|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Deklaruje fabryki klas jako [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), domyślnej fabryki klas ATL.|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Deklaruje obiekt fabryki klas jako fabryki klas.|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) jako fabryki klas.|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabryki klas.|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) jako fabryki klas.|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Deklaruje wirtualnej `GetControllingUnknown` funkcji.|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Deklaruje, że obiekt nie można agregować.|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Deklaruje, obiekt musi być agregowane.|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Sprawdza, czy wartość nieznany zewnętrzne i deklaruje obiektu się agregowaniu lub nie się agregowaniu, odpowiednio.|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Chroni obiektu zewnętrznego przed usunięciem podczas konstruowania obiektu wewnętrznego.|
|[DECLARE_VIEW_STATUS](#declare_view_status)|Określa stan flagi do kontenera.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="declare_aggregatable"></a>  DECLARE_AGGREGATABLE

Określa, czy obiekt może być agregowany.

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa klasy są definiowane jako się agregowaniu.

### <a name="remarks"></a>Uwagi

[Klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera to makro, aby określić domyślny model agregacji. Aby zastąpić to ustawienie domyślne, określ [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) lub [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) makra w definicji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

##  <a name="declare_classfactory"></a>  DECLARE_CLASSFACTORY

Deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako fabryki klas.

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>Uwagi

[Klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) używa tego makra, aby zadeklarować domyślnej fabryki klas dla obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

##  <a name="ccomclassfactory_class"></a>  Klasa CComClassFactory

Ta klasa implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfejsu.

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Uwagi

`CComClassFactory` implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfejs, który zawiera metody do tworzenia obiektu z określonym identyfikatorem CLSID, jak również blokowanie fabryki klas w pamięci umożliwiające szybsze tworzenie nowych obiektów. `IClassFactory` należy zaimplementować dla każdej klasy, która zarejestrowania w rejestrze systemowym i który przypisania CLSID.

Obiekty ATL zwykle uzyskać fabryki klas, wynikające z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](#declare_classfactory), która deklaruje `CComClassFactory` jako domyślnej fabryki klas. Aby zastąpić to ustawienie domyślne, należy określić jedną z DECLARE_CLASSFACTORY*XXX* makra w definicji klasy. Na przykład [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) makro używa określonej klasie dla fabryki klas:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

Powyższej definicji klasy określa, że `CMyClassFactory` będzie służyć jako obiektu domyślnej fabryki klas. `CMyClassFactory` musi pochodzić od klasy `CComClassFactory` i zastąpić `CreateInstance`.

ATL udostępnia trzy makra, które deklarują fabrykę klas:

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) używa [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), która kontroluje tworzenie za pomocą licencji.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) używa [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), który tworzy obiekty w wielu apartamentach.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) używa [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), który tworzy jeden [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) obiektu.

##  <a name="declare_classfactory_ex"></a>  DECLARE_CLASSFACTORY_EX

Deklaruje `cf` jako fabryki klas.

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>Parametry

*usługi CF*<br/>
[in] Nazwa klasy, który implementuje obiekt fabryki klas.

### <a name="remarks"></a>Uwagi

*Cf* parametru musi pochodzić od klasy [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i zastąpić `CreateInstance` metody.

[Klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) obejmuje [DECLARE_CLASSFACTORY](#declare_classfactory) makra, która określa `CComClassFactory` jako domyślnej fabryki klas. Jednak przy tym — makro DECLARE_CLASSFACTORY_EX w definicji klasy do obiektu, możesz zastąpić to ustawienie domyślne.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

##  <a name="declare_classfactory2"></a>  DECLARE_CLASSFACTORY2

Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) jako fabryki klas.

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>Parametry

*— Umowa licencyjna*<br/>
[in] Klasa, która implementuje `VerifyLicenseKey`, `GetLicenseKey`, i `IsLicenseValid`.

### <a name="remarks"></a>Uwagi

[Klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) obejmuje [DECLARE_CLASSFACTORY](#declare_classfactory) makra, która określa [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślnej fabryki klas. Jednak przy tym — makro DECLARE_CLASSFACTORY2 w definicji klasy do obiektu, możesz zastąpić to ustawienie domyślne.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

##  <a name="ccomclassfactory2_class"></a>  Klasa CComClassFactory2

Ta klasa implementuje [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) interfejsu.

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>Parametry

*Licencja*<br/>
Klasa, która implementuje następujące funkcje statyczne:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>Uwagi

`CComClassFactory2` implementuje [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) interfejs, który jest rozszerzeniem programu [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2` Tworzenie obiektów kontrolki za pomocą licencji. Fabryki klas na maszynie licencjonowane wykonywania może zapewnić klucz licencji czasu wykonywania. Ten klucz licencji umożliwia aplikacji do tworzenia wystąpień obiektów, gdy licencja pełną maszyny nie istnieje.

Obiekty ATL zwykle uzyskać fabryki klas, wynikające z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](#declare_classfactory), która deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślnej fabryki klas. Aby użyć `CComClassFactory2`, określ [DECLARE_CLASSFACTORY2](#declare_classfactory2) makra w definicji klasy do obiektu. Na przykład:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`, parametr szablonu `CComClassFactory2`, należy zaimplementować funkcje statyczne `VerifyLicenseKey`, `GetLicenseKey`, i `IsLicenseValid`. Oto przykład klasy proste licencji:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2` pochodzi z obu `CComClassFactory2Base` i *licencji*. `CComClassFactory2Base`, z kolei pochodzi od klasy `IClassFactory2` i **CComObjectRootEx\< CComGlobalsThreadModel >**.

##  <a name="declare_classfactory_auto_thread"></a>  DECLARE_CLASSFACTORY_AUTO_THREAD

Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabryki klas.

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>Uwagi

[Klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) obejmuje [DECLARE_CLASSFACTORY](#declare_classfactory) makra, która określa [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślnej fabryki klas. Jednak przy tym — makro DECLARE_CLASSFACTORY_AUTO_THREAD w definicji klasy do obiektu, możesz zastąpić to ustawienie domyślne.

Podczas tworzenia obiektów w apartamentach wiele (w serwerze procesem), należy dodać DECLARE_CLASSFACTORY_AUTO_THREAD do swojej klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

##  <a name="ccomclassfactoryautothread_class"></a>  Klasa CComClassFactoryAutoThread

Ta klasa implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfejs i umożliwia tworzenie w apartamentach wielu obiektów.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Uwagi

`CComClassFactoryAutoThread` jest podobny do [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ale pozwala na tworzenie w apartamentach wielu obiektów. Aby móc korzystać z tej obsługi, pochodzi z modułu EXE z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Obiekty ATL zwykle uzyskać fabryki klas, wynikające z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](#declare_classfactory), która deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślnej fabryki klas. Aby użyć `CComClassFactoryAutoThread`, określ [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) makra w definicji klasy do obiektu. Na przykład:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

##  <a name="declare_classfactory_singleton"></a>  DECLARE_CLASSFACTORY_SINGLETON

Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) jako fabryki klas.

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>Parametry

*obj*<br/>
[in] Nazwa obiektu klasy.

### <a name="remarks"></a>Uwagi

[Klasy CComCoClass](../../atl/reference/ccomcoclass-class.md) obejmuje [DECLARE_CLASSFACTORY](#declare_classfactory) makra, która określa [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślnej fabryki klas. Jednak przy tym — makro DECLARE_CLASSFACTORY_SINGLETON w definicji klasy do obiektu, możesz zastąpić to ustawienie domyślne.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

##  <a name="ccomclassfactorysingleton_class"></a>  Klasa CComClassFactorySingleton

Ta klasa jest pochodną [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) skonstruowanie pojedynczego obiektu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa.

`CComClassFactorySingleton` pochodzi od klasy [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) skonstruowanie pojedynczego obiektu. Każde wywołanie `CreateInstance` metoda po prostu wysyła zapytanie dotyczące wskaźnika interfejsu tego obiektu.

### <a name="remarks"></a>Uwagi

Obiekty ATL zwykle uzyskać fabryki klas, wynikające z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](#declare_classfactory), która deklaruje `CComClassFactory` jako domyślnej fabryki klas. Aby użyć `CComClassFactorySingleton`, określ [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) makra w definicji klasy do obiektu. Na przykład:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

##  <a name="declare_get_controlling_unknown"></a>  DECLARE_GET_CONTROLLING_UNKNOWN

Deklaruje funkcję wirtualną `GetControllingUnknown`.

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>Uwagi

Dodaj makro do obiektu, jeśli otrzymasz komunikat o błędzie kompilatora `GetControllingUnknown` jest niezdefiniowana (na przykład w `CComAggregateCreator`).

##  <a name="declare_not_aggregatable"></a>  DECLARE_NOT_AGGREGATABLE

Określa, że obiekt nie można agregować.

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa obiektu klasy, które są definiowane jako nie się agregowaniu.

### <a name="remarks"></a>Uwagi

Powoduje, że DECLARE_NOT_AGGREGATABLE `CreateInstance` zostać zwrócony błąd (CLASS_E_NOAGGREGATION), jeśli zostanie podjęta próba do zagregowania na obiekt.

Domyślnie [CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera [DECLARE_AGGREGATABLE](#declare_aggregatable) makra, która określa, czy obiekt może być agregowany. Aby zastąpić to zachowanie domyślne, należy dołączyć DECLARE_NOT_AGGREGATABLE w definicji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

##  <a name="declare_only_aggregatable"></a>  DECLARE_ONLY_AGGREGATABLE

Określa, czy obiekt musi być agregowana.

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa obiektu klasy, które są definiowane jako tylko się agregowaniu.

### <a name="remarks"></a>Uwagi

DECLARE_ONLY_AGGREGATABLE powoduje błąd (E_FAIL), jeśli zostanie podjęta próba `CoCreate` obiektu jako obiektu nieagregowane.

Domyślnie [CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera [DECLARE_AGGREGATABLE](#declare_aggregatable) makra, która określa, czy obiekt może być agregowany. Aby zastąpić to zachowanie domyślne, należy dołączyć DECLARE_ONLY_AGGREGATABLE w definicji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

##  <a name="declare_poly_aggregatable"></a>  DECLARE_POLY_AGGREGATABLE

Określa, że wystąpienie **CComPolyObject \<**  *x* **>** jest tworzony po utworzeniu obiektu.

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa obiektu klasy są definiowane jako się agregowaniu lub nie się agregowaniu.

### <a name="remarks"></a>Uwagi

Podczas tworzenia jest sprawdzany wartość zewnętrzne nieznany. Jeśli ma wartość NULL, `IUnknown` został zaimplementowany dla obiektu nieagregowane. Jeśli nieznany zewnętrzny nie ma wartość NULL, `IUnknown` został zaimplementowany dla obiektu zagregowanego.

Zaletą używania DECLARE_POLY_AGGREGATABLE to uniknąć konieczności zarówno `CComAggObject` i `CComObject` w module sposób obsługiwać przypadki zagregowane i nieagregowane. Pojedynczy `CComPolyObject` obiektu obsługuje w obu przypadkach. Oznacza to, że tylko jedna kopia vtable i jedną kopię funkcje istnieją w module. Jeśli Twoje vtable jest duży, to znacznie zmniejszyć rozmiar modułu. Jednak jeśli Twoja vtable jest mały, za pomocą `CComPolyObject` może spowodować nieco większy rozmiar modułu, ponieważ nie jest zoptymalizowana do zagregowanych lub nieagregowane obiektu, ponieważ są `CComAggObject` i `CComObject`.

Makra DECLARE_POLY_AGGREGATABLE automatycznie jest zadeklarowany w obiekcie, jeśli używasz Kreator kontrolki ATL, aby utworzyć pełną kontrolę.

##  <a name="declare_protect_final_construct"></a>  DECLARE_PROTECT_FINAL_CONSTRUCT

Chroni obiekt przed usunięciem Jeśli (podczas [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) wewnętrznego obiektu zagregowanego zwiększa liczbę odwołań, a następnie zmniejsza liczbę na wartość 0.

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

##  <a name="declare_view_status"></a>  DECLARE_VIEW_STATUS

Umieść tego makra w klasie kontrolki kontrolkę ActiveX biblioteki ATL, aby określić stan flagi do kontenera.

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>Parametry

*statusFlags*<br/>
[in] Stan flagi. Zobacz [stan](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus) listę flag.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
