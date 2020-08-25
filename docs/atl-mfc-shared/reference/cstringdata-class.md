---
title: Klasa CStringData
ms.date: 11/04/2016
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
ms.openlocfilehash: 140836f45ed2f4088bc0baed67676f93cb268d01
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832116"
---
# <a name="cstringdata-class"></a>Klasa CStringData

Ta klasa reprezentuje dane obiektu String.

## <a name="syntax"></a>Składnia

```
struct CStringData
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|Nazwa|Opis|
|-|-|
|[AddRef](#addref)|Zwiększa liczbę odwołań obiektu danych ciągu.|
|[data](#data)|Pobiera dane znakowe obiektu ciągu.|
|[IsLocked](#islocked)|Określa, czy bufor skojarzonego obiektu ciągu jest zablokowany.|
|[Nie udostępniono](#isshared)|Określa, czy bufor skojarzonego obiektu ciągu jest aktualnie udostępniony.|
|[Skręt](#lock)|Blokuje bufor skojarzonego obiektu ciągu.|
|[Wersja](#release)|Zwalnia określony obiekt ciągu.|
|[Odblokowania](#unlock)|Odblokowuje bufor skojarzonego obiektu ciągu.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|-|-|
|[nAllocLength](#nalloclength)|Długość przyznanych danych w `XCHAR` s (bez uwzględniania kończących wartości null)|
|[nDataLength](#ndatalength)|Długość aktualnie używanych danych w `XCHAR` s (bez uwzględniania kończących wartości null)|
|[nRefs](#nrefs)|Bieżąca liczba odwołań obiektu.|
|[pStringMgr](#pstringmgr)|Wskaźnik do Menedżera ciągów dla tego obiektu ciągu.|

## <a name="remarks"></a>Uwagi

Ta klasa powinna być używana tylko przez deweloperów implementujących niestandardowych menedżerów ciągów. Aby uzyskać więcej informacji na temat niestandardowych menedżerów ciągów, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

Ta klasa hermetyzuje różne typy informacji i danych związanych z wyższym obiektem ciągu, takimi jak [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)lub [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) . Każdy wyższy obiekt ciągu zawiera wskaźnik do skojarzonego `CStringData` obiektu, dzięki czemu wiele obiektów String może wskazywać na ten sam obiekt danych ciągu. Ta relacja jest reprezentowana przez liczbę odwołań ( `nRefs` ) `CStringData` obiektu.

> [!NOTE]
> W niektórych przypadkach typ ciągu (taki jak `CFixedString` ) nie będzie współużytkować obiektu danych ciągu z więcej niż jednym większym obiektem ciągu. Aby uzyskać więcej informacji na ten temat, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

Te dane składają się z:

- Menedżer pamięci (typu [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) ciągu.

- Bieżąca długość ( [nDataLength](#ndatalength)) ciągu.

- Przydzieloną Długość ( [nAllocLength](#nalloclength)) ciągu. Ze względu na wydajność może się to różnić od bieżącej długości ciągu

- Bieżąca liczba odwołań ( [nRefs](#nrefs)) `CStringData` obiektu. Ta wartość jest używana podczas określania, ile obiektów String korzysta z tego samego `CStringData` obiektu.

- Faktyczny bufor znaków ( [dane](#data)) ciągu.

   > [!NOTE]
   > Faktyczny bufor znaków obiektu String jest przypisywany przez Menedżera ciągów i jest dołączany do `CStringData` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr. h

## <a name="cstringdataaddref"></a><a name="addref"></a> CStringData:: AddRef

Zwiększa liczbę odwołań obiektu ciągu.

```cpp
void AddRef() throw();
```

### <a name="remarks"></a>Uwagi

Zwiększa liczbę odwołań obiektu ciągu.

> [!NOTE]
> Nie wywołuj tej metody na ciąg z ujemną liczbą odwołań, ponieważ liczba ujemna wskazuje, że bufor ciągu jest zablokowany.

## <a name="cstringdatadata"></a><a name="data"></a> CStringData::d ATA

Zwraca wskaźnik do buforu znaków obiektu ciągu.

```cpp
void* data() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu znaków obiektu ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zwrócić bieżący bufor znaków skojarzonego obiektu ciągu.

> [!NOTE]
> Ten bufor nie jest przypisywany przez `CStringData` obiekt, ale przez Menedżera ciągów w razie konieczności. Po przydzieleniu bufor jest dołączany do obiektu danych ciągu.

## <a name="cstringdataislocked"></a><a name="islocked"></a> CStringData:: IsLocked

Określa, czy bufor znaków jest zablokowany.

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli bufor jest zablokowany; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby określić, czy bufor znaku obiektu ciągu jest aktualnie zablokowany.

## <a name="cstringdataisshared"></a><a name="isshared"></a> CStringData:: IsShared

Określa, czy bufor znaków jest udostępniony.

```
bool IsShared() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli bufor jest udostępniony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby określić, czy bufor znaków obiektu danych ciągu jest obecnie współużytkowany przez wiele obiektów ciągu.

## <a name="cstringdatalock"></a><a name="lock"></a> CStringData:: Lock

Blokuje bufor znaków skojarzonego obiektu ciągu.

```cpp
void Lock() throw();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zablokować bufor znaków obiektu danych ciągu. Blokowanie i odblokowywanie jest stosowane, gdy deweloper ma bezpośredni dostęp do buforu znaków. Dobrym przykładem blokowania jest wykaz metod [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) i [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) `CSimpleStringT` .

> [!NOTE]
> Bufor znaków można zablokować tylko wtedy, gdy bufor nie jest współużytkowany przez więcej obiektów ciągu.

## <a name="cstringdatanalloclength"></a><a name="nalloclength"></a> CStringData::nAllocLength

Długość przydzieloną buforu znaków.

```
int nAllocLength;
```

### <a name="remarks"></a>Uwagi

Przechowuje wyrażoną w s długość przydzieloną bufora danych `XCHAR` (bez uwzględnienia zakończenia wartości null).

## <a name="cstringdatandatalength"></a><a name="ndatalength"></a> CStringData::nDataLength

Bieżąca długość obiektu ciągu.

```
int nDataLength;
```

### <a name="remarks"></a>Uwagi

Przechowuje wyrażoną w liczbie długość aktualnie używanych danych `XCHAR` (bez uwzględnienia kończących wartości null).

## <a name="cstringdatanrefs"></a><a name="nrefs"></a> CStringData::nRefs

Liczba odwołań do obiektu danych ciągu.

```
long nRefs;
```

### <a name="remarks"></a>Uwagi

Przechowuje liczbę odwołań obiektu danych ciągu. Ta liczba wskazuje liczbę obiektów z większym ciągiem, które są skojarzone z obiektem danych ciągu. Wartość ujemna wskazuje, że obiekt danych ciągu jest aktualnie zablokowany.

## <a name="cstringdatapstringmgr"></a><a name="pstringmgr"></a> CStringData::p StringMgr

Menedżer pamięci skojarzonego obiektu ciągu.

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>Uwagi

Przechowuje Menedżera pamięci dla skojarzonego obiektu ciągu. Aby uzyskać więcej informacji o menedżerach pamięci i ciągach, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringdatarelease"></a><a name="release"></a> CStringData:: Release

Zmniejsza liczbę odwołań obiektu danych ciągu.

```cpp
void Release() throw();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zmniejszyć liczbę odwołań, zwalniając `CStringData` strukturę, jeśli liczba odwołań trafi zero. Jest to często wykonywane, gdy obiekt String jest usuwany i dlatego nie musi już odwoływać się do obiektu danych ciągu.

Na przykład następujący kod wywoła `CStringData::Release` dla obiektu danych ciągu skojarzonego z `str1` :

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

## <a name="cstringdataunlock"></a><a name="unlock"></a> CStringData:: Unlock

Odblokowuje bufor znaków skojarzonego obiektu ciągu.

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby odblokować bufor znaków obiektu danych ciągu. Po odblokowaniu bufora jest możliwe do udostępnienia i może być liczony jako odwołanie.

> [!NOTE]
> Każde wywołanie `Lock` musi być dopasowane przez odpowiadające mu wywołanie `Unlock` .

Blokowanie i odblokowywanie jest używane, gdy Deweloper musi upewnić się, że dane ciągu nie są udostępniane. Dobrym przykładem blokowania jest wykaz metod [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) i [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) `CSimpleStringT` .

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
