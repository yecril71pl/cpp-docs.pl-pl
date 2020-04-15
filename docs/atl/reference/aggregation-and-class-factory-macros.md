---
title: Makra fabryczne agregacji i klasy
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
ms.openlocfilehash: 33f33043d1a2c824ada26399365541796178d21d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319336"
---
# <a name="aggregation-and-class-factory-macros"></a>Makra fabryczne agregacji i klasy

Te makra zapewniają sposoby kontrolowania agregacji i deklarowania fabryk klas.

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Deklaruje, że obiekt może być agregowany (domyślnie).|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Deklaruje fabrykę klas jako [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), fabrykę klas domyślnych ATL.|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Deklaruje, że obiekt fabryki klasy jest fabryką klas.|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) do fabryki klas.|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) do fabryki klas.|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) do fabryki klas.|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Deklaruje funkcję `GetControllingUnknown` wirtualną.|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Deklaruje, że obiekt nie może być agregowane.|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Deklaruje, że obiekt musi być agregowane.|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Sprawdza wartość zewnętrznego nieznanego i deklaruje, że obiekt można agregować lub nie można go odpowiednio agregować.|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Chroni obiekt zewnętrzny przed usunięciem podczas budowy obiektu wewnętrznego.|
|[DECLARE_VIEW_STATUS](#declare_view_status)|Określa flagi VIEWSTATUS do kontenera.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE

Określa, że obiekt może być agregowany.

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa klasy, którą definiujesz jako agregowalną.

### <a name="remarks"></a>Uwagi

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera to makro, aby określić domyślny model agregacji. Aby zastąpić tę wartość domyślną, należy określić [makro DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) lub [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) w definicji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a>DECLARE_CLASSFACTORY

Deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) do fabryki klas.

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>Uwagi

[CComCoClass](../../atl/reference/ccomcoclass-class.md) używa tego makra do deklarowania domyślnej fabryki klasy dla obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a>Klasa CComClassFactory

Ta klasa implementuje interfejs [IClassFactory.](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Uwagi

`CComClassFactory`implementuje interfejs [IClassFactory,](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) który zawiera metody tworzenia obiektu określonego identyfikatora CLSID, a także blokowanie fabryki klas w pamięci, aby umożliwić szybkie tworzenie nowych obiektów. `IClassFactory`musi być zaimplementowana dla każdej klasy, która jest rejestrowana w rejestrze systemowym i do której można przypisać CLSID.

Obiekty ATL zwykle nabywają fabrykę klas, wywodząc się z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [makro DECLARE_CLASSFACTORY](#declare_classfactory), `CComClassFactory` który deklaruje jako fabryka klas domyślnych. Aby zastąpić tę wartość domyślną, określ jedno z makr DECLARE_CLASSFACTORY*XXX* w definicji klasy. Na przykład makro [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) używa określonej klasy dla fabryki klas:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

Powyższa definicja klasy `CMyClassFactory` określa, że będzie używany jako fabryka klas domyślnych obiektu. `CMyClassFactory`musi pochodzić `CComClassFactory` od i `CreateInstance`zastąpić .

ATL udostępnia trzy inne makra, które deklarują fabrykę klas:

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) Używa [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), który kontroluje tworzenie za pośrednictwem licencji.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) Używa [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), który tworzy obiekty w wielu mieszkaniach.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) Używa [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), który konstruuje pojedynczy [obiekt CComObjectGlobal.](../../atl/reference/ccomobjectglobal-class.md)

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX

Deklaruje, `cf` że jest fabryką klasy.

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>Parametry

*Por*<br/>
[w] Nazwa klasy, która implementuje obiekt fabryki klasy.

### <a name="remarks"></a>Uwagi

Cf *cf* Parametr musi pochodzić z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) `CreateInstance` i zastąpić metodę.

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera [makro DECLARE_CLASSFACTORY,](#declare_classfactory) które `CComClassFactory` określa jako domyślną fabrykę klas. Jednak dołączając makro DECLARE_CLASSFACTORY_EX do definicji klasy obiektu, należy zastąpić tę wartość domyślną.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2

Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) do fabryki klas.

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>Parametry

*Lic*<br/>
[w] Klasa, która `VerifyLicenseKey`implementuje `GetLicenseKey` `IsLicenseValid`, i .

### <a name="remarks"></a>Uwagi

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera makro [DECLARE_CLASSFACTORY,](#declare_classfactory) który określa [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Jednak dołączając makro DECLARE_CLASSFACTORY2 do definicji klasy obiektu, należy zastąpić tę wartość domyślną.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a>Klasa CComClassFactory2

Ta klasa implementuje interfejs [IClassFactory2.](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>Parametry

*Licencji*<br/>
Klasa, która implementuje następujące funkcje statyczne:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>Uwagi

`CComClassFactory2`implementuje interfejs [IClassFactory2,](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) który jest rozszerzeniem [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`steruje tworzeniem obiektów za pośrednictwem licencji. Fabryczna klasa wykonywana na licencjonowanym komputerze może zapewnić klucz licencji w czasie wykonywania. Ten klucz licencyjny umożliwia aplikacji tworzenie wystąpienia obiektów, gdy pełna licencja komputera nie istnieje.

Obiekty ATL zwykle nabywają fabrykę klas, wywodząc się z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [makro DECLARE_CLASSFACTORY](#declare_classfactory), który deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako fabryka klasy domyślnej. Aby `CComClassFactory2`użyć , określ [makro DECLARE_CLASSFACTORY2](#declare_classfactory2) w definicji klasy obiektu. Przykład:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`, parametr szablonu `CComClassFactory2`do , musi `VerifyLicenseKey` `GetLicenseKey`implementować `IsLicenseValid`funkcje statyczne , i . Oto przykład prostej klasy licencji:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2`pochodzi zarówno `CComClassFactory2Base` z *licencji.* `CComClassFactory2Base`, z kolei, `IClassFactory2` pochodzi z i **\< CComObjectRootEx CComGlobalsThreadModel >**.

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD

Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) do fabryki klas.

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>Uwagi

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera makro [DECLARE_CLASSFACTORY,](#declare_classfactory) który określa [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Jednak dołączając makro DECLARE_CLASSFACTORY_AUTO_THREAD do definicji klasy obiektu, należy zastąpić tę wartość domyślną.

Podczas tworzenia obiektów w wielu mieszkaniach (na serwerze out-of-proc), należy dodać DECLARE_CLASSFACTORY_AUTO_THREAD do klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a>Klasa CComClassFactoryAutoThread, klasa

Ta klasa implementuje interfejs [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) i umożliwia tworzenie obiektów w wielu mieszkaniach.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Uwagi

`CComClassFactoryAutoThread`jest podobny do [CComClassFactory,](../../atl/reference/ccomclassfactory-class.md)ale umożliwia tworzenie obiektów w wielu mieszkaniach. Aby skorzystać z tej pomocy technicznej, należy wykorzystać z modułu EXE z [modułu CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Obiekty ATL zwykle nabywają fabrykę klas, wywodząc się z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [makro DECLARE_CLASSFACTORY](#declare_classfactory), który deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako fabryka klasy domyślnej. Aby `CComClassFactoryAutoThread`użyć , określ [makro DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) w definicji klasy obiektu. Przykład:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON

Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) do fabryki klas.

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>Parametry

*Obj*<br/>
[w] Nazwa obiektu klasy.

### <a name="remarks"></a>Uwagi

[CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera makro [DECLARE_CLASSFACTORY,](#declare_classfactory) który określa [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Jednak dołączając makro DECLARE_CLASSFACTORY_SINGLETON do definicji klasy obiektu, należy zastąpić tę wartość domyślną.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a>Klasa CComClassFactorySingleton

Ta klasa pochodzi z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa.

`CComClassFactorySingleton`pochodzi z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu. Każde wywołanie `CreateInstance` metody po prostu wysyła zapytanie do tego obiektu dla wskaźnika interfejsu.

### <a name="remarks"></a>Uwagi

Obiekty ATL zwykle nabywają fabrykę klas, wywodząc się z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [makro DECLARE_CLASSFACTORY](#declare_classfactory), `CComClassFactory` który deklaruje jako fabryka klas domyślnych. Aby `CComClassFactorySingleton`użyć , określ [makro DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) w definicji klasy obiektu. Przykład:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN

Deklaruje funkcję `GetControllingUnknown`wirtualną .

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>Uwagi

Dodaj to makro do obiektu, jeśli zostanie `GetControllingUnknown` wyświetlony niezdefiniowany komunikat `CComAggregateCreator`o błędzie kompilatora (na przykład w ).

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE

Określa, że nie można agregować obiektu.

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa obiektu klasy, który definiujesz jako nie agregowalny.

### <a name="remarks"></a>Uwagi

DECLARE_NOT_AGGREGATABLE powoduje `CreateInstance` zwrócenie błędu (CLASS_E_NOAGGREGATION), jeśli zostanie podjęta próba agregacji do obiektu.

Domyślnie [CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera [makro DECLARE_AGGREGATABLE,](#declare_aggregatable) który określa, że obiekt może być agregowane. Aby zastąpić to zachowanie domyślne, uwzględnij DECLARE_NOT_AGGREGATABLE w definicji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE

Określa, że obiekt musi być agregowany.

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa obiektu klasy, który definiujesz jako tylko agregowalne.

### <a name="remarks"></a>Uwagi

DECLARE_ONLY_AGGREGATABLE powoduje błąd (E_FAIL), jeśli zostanie podjęta próba `CoCreate` obiektu jako obiektu nieagregowanego.

Domyślnie [CComCoClass](../../atl/reference/ccomcoclass-class.md) zawiera [makro DECLARE_AGGREGATABLE,](#declare_aggregatable) który określa, że obiekt może być agregowane. Aby zastąpić to zachowanie domyślne, uwzględnij DECLARE_ONLY_AGGREGATABLE w definicji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE

Określa, że podczas tworzenia obiektu jest tworzone wystąpienie ** \< CComPolyObject** *x.* **>**

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa obiektu klasy, który definiujesz jako agregowalne lub nie agregowalne.

### <a name="remarks"></a>Uwagi

Podczas tworzenia sprawdzana jest wartość zewnętrznej nieznanej. Jeśli jest null, `IUnknown` jest zaimplementowana dla obiektu nieagregowanego. Jeśli zewnętrzna niewiadoma nie jest null, `IUnknown` jest implementowana dla zagregowanego obiektu.

Zaletą korzystania z DECLARE_POLY_AGGREGATABLE jest unikanie `CComAggObject` posiadania `CComObject` zarówno i w module do obsługi zagregowanych i nieagregowanych spraw. Pojedynczy `CComPolyObject` obiekt obsługuje obie sprawy. Oznacza to, że tylko jedna kopia vtable i jedna kopia funkcji istnieje w module. Jeśli twój vtable jest duży, może to znacznie zmniejszyć rozmiar modułu. Jeśli jednak tabela vtable `CComPolyObject` jest mała, użycie może spowodować nieco większy rozmiar modułu, ponieważ nie jest `CComAggObject` zoptymalizowany pod kątem zagregowanego lub nieagregowanego obiektu, tak jak są i `CComObject`.

Makro DECLARE_POLY_AGGREGATABLE jest automatycznie deklarowane w obiekcie, jeśli do utworzenia pełnego formantu jest używany Kreator sterowania ATL.

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT

Chroni obiekt przed usunięciem, jeśli (podczas [FinalConstruct)](ccomobjectrootex-class.md#finalconstruct)wewnętrzny obiekt zagregowany zwiększa liczbę odwołań, a następnie zmniejsza liczbę do 0.

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a>DECLARE_VIEW_STATUS

Umieść to makro w klasie formantu ACTIVEX ATL, aby określić flagi VIEWSTATUS w kontenerze.

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>Parametry

*statusPłagi*<br/>
[w] Flagi VIEWSTATUS. Zobacz [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) listę flag.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
