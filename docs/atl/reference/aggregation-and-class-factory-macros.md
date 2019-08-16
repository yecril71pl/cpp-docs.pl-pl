---
title: Makra agregacji i fabryki klas
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
ms.openlocfilehash: 38239942b99a29b5777deef8000d9f1ab85b10e6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492200"
---
# <a name="aggregation-and-class-factory-macros"></a>Makra agregacji i fabryki klas

Te makra zapewniają sposoby kontrolowania agregacji i deklarowania fabryk klas.

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Deklaruje, że obiekt może być zagregowany (wartość domyślna).|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Deklaruje fabrykę klas jako [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), domyślną fabrykę klas ATL.|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Deklaruje obiekt fabryki klas jako fabrykę klas.|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) jako fabrykę klas.|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabrykę klas.|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) jako fabrykę klas.|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Deklaruje funkcję `GetControllingUnknown` wirtualną.|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Deklaruje, że nie można agregować obiektu.|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Deklaruje, że obiekt musi być zagregowany.|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Sprawdza wartość elementu zewnętrznego nieznanego i deklaruje obiekt do agregowania lub nie można wykonać agregowania, zgodnie z potrzebami.|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Chroni obiekt zewnętrzny przed usunięciem podczas konstruowania obiektu wewnętrznego.|
|[DECLARE_VIEW_STATUS](#declare_view_status)|Określa flagi podwójne do kontenera.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE

Określa, że obiekt może być zagregowany.

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
podczas Nazwa klasy, która jest definiowana do agregowania.

### <a name="remarks"></a>Uwagi

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera to makro, aby określić domyślny model agregacji. Aby zastąpić to ustawienie domyślne, w definicji klasy należy określić makro [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) lub [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

##  <a name="declare_classfactory"></a>DECLARE_CLASSFACTORY

Deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako fabrykę klas.

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>Uwagi

[CComCoClass](../../atl/reference/ccomcoclass-class.md) używa tego makra do deklarowania domyślnej fabryki klas dla obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

##  <a name="ccomclassfactory_class"></a>Klasa CComClassFactory

Ta klasa implementuje interfejs [elementu IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) .

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Uwagi

`CComClassFactory`implementuje interfejs [elementu IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) , który zawiera metody tworzenia obiektu określonego identyfikatora CLSID, a także blokowania fabryki klas w pamięci, aby umożliwić szybsze tworzenie nowych obiektów. `IClassFactory`należy zaimplementować dla każdej klasy, która jest zarejestrowana w rejestrze systemowym i do której przypisany jest identyfikator CLSID.

Obiekty ATL zwykle uzyskują fabrykę klasy poprzez wyprowadzanie z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [DECLARE_CLASSFACTORY](#declare_classfactory)makro, które deklaruje `CComClassFactory` jako domyślną fabrykę klas. Aby zastąpić to ustawienie domyślne, należy określić jedno z makr DECLARE_CLASSFACTORY*XXX* w definicji klasy. Na przykład makro [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) używa określonej klasy dla fabryki klas:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

Powyższa definicja klasy określa, `CMyClassFactory` że będzie używana jako domyślna fabryka klas obiektu. `CMyClassFactory`musi pochodzić od `CComClassFactory` i override `CreateInstance`.

ATL udostępnia trzy inne makra, które deklarują fabrykę klasy:

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) Używa [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), który kontroluje tworzenie za pośrednictwem licencji.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) Używa [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), który tworzy obiekty w wielu apartamentachach.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) Używa [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), który konstruuje pojedynczy obiekt [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) .

##  <a name="declare_classfactory_ex"></a>  DECLARE_CLASSFACTORY_EX

Deklaruje `cf` , że należy do fabryki klas.

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>Parametry

*cf*<br/>
podczas Nazwa klasy implementującej obiekt fabryki klas.

### <a name="remarks"></a>Uwagi

Parametr *CF* musi pochodzić od [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) `CreateInstance` i zastąpić metodę.

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera makro [DECLARE_CLASSFACTORY](#declare_classfactory) , które określa `CComClassFactory` jako domyślną fabrykę klas. Jednak przez dołączenie makra DECLARE_CLASSFACTORY_EX w definicji klasy obiektu, to ustawienie domyślne zostanie zastąpione.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

##  <a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2

Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) jako fabrykę klas.

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>Parametry

*lic*<br/>
podczas Klasa, która implementuje `VerifyLicenseKey`, `GetLicenseKey`, i `IsLicenseValid`.

### <a name="remarks"></a>Uwagi

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera makro [DECLARE_CLASSFACTORY](#declare_classfactory) , które określa [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Jednak przez dołączenie makra DECLARE_CLASSFACTORY2 w definicji klasy obiektu, to ustawienie domyślne zostanie zastąpione.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

##  <a name="ccomclassfactory2_class"></a>Klasa CComClassFactory2

Ta klasa implementuje interfejs [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) .

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>Parametry

*licencjonowan*<br/>
Klasa, która implementuje następujące funkcje statyczne:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>Uwagi

`CComClassFactory2`implementuje interfejs [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) , który jest rozszerzeniem [elementu IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`steruje tworzeniem obiektów za pomocą licencji. Fabryka klas wykonywana na licencjonowanym komputerze może zapewnić klucz licencji w czasie wykonywania. Ten klucz licencji pozwala aplikacji na tworzenie wystąpień obiektów w przypadku, gdy nie istnieje pełna licencja komputera.

Obiekty ATL zwykle uzyskują fabrykę klasy poprzez wyprowadzanie z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [DECLARE_CLASSFACTORY](#declare_classfactory)makro, które deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Aby użyć `CComClassFactory2`, określ makro [DECLARE_CLASSFACTORY2](#declare_classfactory2) w definicji klasy obiektu. Przykład:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`, parametr szablonu `CComClassFactory2`do, musi implementować funkcje `VerifyLicenseKey`statyczne, `GetLicenseKey`i `IsLicenseValid`. Oto przykład prostej klasy licencji:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2`pochodzi od obu `CComClassFactory2Base` *licencji*. `CComClassFactory2Base`z kolei pochodzi od `IClassFactory2` i **CComObjectRootEx\< CComGlobalsThreadModel >** .

##  <a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD

Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabrykę klas.

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>Uwagi

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera makro [DECLARE_CLASSFACTORY](#declare_classfactory) , które określa [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Jednak przez dołączenie makra DECLARE_CLASSFACTORY_AUTO_THREAD w definicji klasy obiektu, to ustawienie domyślne zostanie zastąpione.

Podczas tworzenia obiektów w wielu apartamentach (na serwerze out-of-proc) Dodaj DECLARE_CLASSFACTORY_AUTO_THREAD do swojej klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

##  <a name="ccomclassfactoryautothread_class"></a>Klasa CComClassFactoryAutoThread

Ta klasa implementuje interfejs [elementu IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) i umożliwia tworzenie obiektów w wielu apartamentachach.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Uwagi

`CComClassFactoryAutoThread`jest podobny do [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ale umożliwia tworzenie obiektów w wielu apartamentachach. Aby skorzystać z tej obsługi, należy utworzyć moduł EXE z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Obiekty ATL zwykle uzyskują fabrykę klasy poprzez wyprowadzanie z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [DECLARE_CLASSFACTORY](#declare_classfactory)makro, które deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Aby użyć `CComClassFactoryAutoThread`, określ makro [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) w definicji klasy obiektu. Przykład:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

##  <a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON

Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) jako fabrykę klas.

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>Parametry

*obj*<br/>
podczas Nazwa obiektu klasy.

### <a name="remarks"></a>Uwagi

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera makro [DECLARE_CLASSFACTORY](#declare_classfactory) , które określa [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Jednak przez dołączenie makra DECLARE_CLASSFACTORY_SINGLETON w definicji klasy obiektu, to ustawienie domyślne zostanie zastąpione.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

##  <a name="ccomclassfactorysingleton_class"></a>Klasa CComClassFactorySingleton

Ta klasa pochodzi z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa.

`CComClassFactorySingleton`pochodzi z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu. Każde wywołanie `CreateInstance` metody po prostu wysyła zapytanie do tego obiektu dla wskaźnika interfejsu.

### <a name="remarks"></a>Uwagi

Obiekty ATL zwykle uzyskują fabrykę klasy poprzez wyprowadzanie z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [DECLARE_CLASSFACTORY](#declare_classfactory)makro, które deklaruje `CComClassFactory` jako domyślną fabrykę klas. Aby użyć `CComClassFactorySingleton`, określ makro [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) w definicji klasy obiektu. Na przykład:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

##  <a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN

Deklaruje funkcję `GetControllingUnknown`wirtualną.

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>Uwagi

Dodaj to makro do obiektu, jeśli zostanie wyświetlony komunikat o błędzie kompilatora, `GetControllingUnknown` który jest niezdefiniowany (na przykład `CComAggregateCreator`w programie).

##  <a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE

Określa, że nie można agregować obiektu.

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
podczas Nazwa obiektu klasy, który jest definiowany jako niepoddający się agregowaniu.

### <a name="remarks"></a>Uwagi

DECLARE_NOT_AGGREGATABLE powoduje `CreateInstance` zwrócenie błędu (CLASS_E_NOAGGREGATION), Jeśli podjęto próbę agregacji do obiektu.

Domyślnie [CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera makro [DECLARE_AGGREGATABLE](#declare_aggregatable) , które określa, że obiekt może być zagregowany. Aby zastąpić to zachowanie domyślne, należy uwzględnić DECLARE_NOT_AGGREGATABLE w definicji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

##  <a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE

Określa, że obiekt musi być zagregowany.

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
podczas Nazwa obiektu klasy, który definiujesz jako do agregowania.

### <a name="remarks"></a>Uwagi

DECLARE_ONLY_AGGREGATABLE powoduje błąd (E_FAIL), jeśli podjęta zostanie próba do `CoCreate` obiektu jako obiekt niezagregowany.

Domyślnie [CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera makro [DECLARE_AGGREGATABLE](#declare_aggregatable) , które określa, że obiekt może być zagregowany. Aby zastąpić to zachowanie domyślne, należy uwzględnić DECLARE_ONLY_AGGREGATABLE w definicji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

##  <a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE

Określa, że wystąpienie **CComPolyObject \<**  *x* **>** jest tworzone podczas tworzenia obiektu.

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*x*<br/>
podczas Nazwa obiektu klasy, który jest definiowany jako agregowany lub nieagregowany.

### <a name="remarks"></a>Uwagi

Podczas tworzenia jest sprawdzana wartość nieznanego elementu zewnętrznego. Jeśli ma wartość null, `IUnknown` jest zaimplementowana dla niezagregowanego obiektu. Jeśli nieznana zewnętrzna nie ma wartości null `IUnknown` , jest zaimplementowana dla obiektu agregowanego.

Zaletą korzystania z DECLARE_POLY_AGGREGATABLE jest unikanie, aby oba `CComAggObject` i `CComObject` w module obsługiwały zagregowane i niezagregowane przypadki. Pojedynczy `CComPolyObject` obiekt obsługuje oba przypadki. Oznacza to, że w module istnieją tylko jedną kopię tabeli metod wirtualnych i jedną kopię funkcji. W przypadku dużej liczby tablic wirtualnych może to znacznie zmniejszyć rozmiar modułu. Jeśli jednak tablica tablicowa jest mała, użycie `CComPolyObject` może spowodować nieco większy rozmiar modułu, ponieważ nie jest zoptymalizowany pod kątem zagregowanych lub niezagregowanych obiektów, ponieważ są `CComAggObject` i `CComObject`.

Makro DECLARE_POLY_AGGREGATABLE jest automatycznie deklarowane w obiekcie, jeśli używasz Kreatora kontrolki ATL do utworzenia pełnej kontroli.

##  <a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT

Chroni obiekt przed usunięciem, jeśli (w trakcie [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) wewnętrzny zagregowany obiekt zwiększa liczbę odwołań, a następnie zmniejsza liczbę do 0.

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

##  <a name="declare_view_status"></a>DECLARE_VIEW_STATUS

Umieść to makro w klasie Control formantu ActiveX ATL, aby określić flagi podwójne do kontenera.

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>Parametry

*statusFlags*<br/>
podczas Flagi podwójne. Zobacz [podwójne](/windows/win32/api/ocidl/ne-ocidl-viewstatus) , aby zapoznać się z listą flag.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>Zobacz także

[Utworze](../../atl/reference/atl-macros.md)
