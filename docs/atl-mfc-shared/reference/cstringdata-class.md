---
title: CStringData, klasa
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
ms.openlocfilehash: f14f1d9c269f06099bd224f582de1f55da33ff0f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746837"
---
# <a name="cstringdata-class"></a>CStringData, klasa

Ta klasa reprezentuje dane obiektu ciągu.

## <a name="syntax"></a>Składnia

```
struct CStringData
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Addref](#addref)|Zwiększa liczbę odwołań obiektu danych ciągu.|
|[Danych](#data)|Pobiera dane znaków obiektu ciągu.|
|[Islocked](#islocked)|Określa, czy bufor skojarzonego obiektu ciągu jest zablokowany.|
|[Isshared](#isshared)|Określa, czy bufor skojarzonego obiektu ciągu jest aktualnie udostępniony.|
|[Blokady](#lock)|Blokuje bufor skojarzonego obiektu ciągu.|
|[Release](#release)|Zwalnia określony obiekt ciągu.|
|[Odblokować](#unlock)|Odblokowuje bufor skojarzonego obiektu ciągu.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[nAllocLength (Niem.](#nalloclength)|Długość przydzielonych `XCHAR`danych w s (z wyłączeniem zakończenia wartości null)|
|[nDanyLength](#ndatalength)|Długość aktualnie używanych `XCHAR`danych w s (z wyłączeniem zakończenia wartości null)|
|[nRefs (Odblaski)](#nrefs)|Bieżąca liczba odwołań obiektu.|
|[pStringMgr](#pstringmgr)|Wskaźnik do menedżera ciągów tego obiektu ciągu.|

## <a name="remarks"></a>Uwagi

Ta klasa powinna być używana tylko przez deweloperów implementujących menedżerów ciągów niestandardowych. Aby uzyskać więcej informacji na temat niestandardowych menedżerów ciągów, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

Ta klasa hermetyzuje różne typy informacji i danych skojarzonych z obiektem wyższego ciągu, takie jak [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)lub [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) obiektów. Każdy obiekt wyższego ciągu zawiera wskaźnik `CStringData` do skojarzonego obiektu, dzięki czemu wiele obiektów ciągów wskazuje ten sam obiekt danych ciągu. Ta relacja jest reprezentowana przez`nRefs`liczbę `CStringData` odwołań ( ) obiektu.

> [!NOTE]
> W niektórych przypadkach typ ciągu `CFixedString`(na przykład ) nie będzie współdzielić obiektu danych ciągu z więcej niż jednym obiektem wyższego ciągu. Aby uzyskać więcej informacji na ten temat, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

Dane te składają się z:

- Menedżer pamięci (typu [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) ciągu.

- Bieżąca długość ( [nDataLength](#ndatalength)) ciągu.

- Przydzielona długość ( [nAllocLength](#nalloclength)) ciągu. Ze względu na wydajność może to różnić się od bieżącej długości ciągu

- Bieżąca liczba odwołań ( [nRefs](#nrefs)) `CStringData` obiektu. Ta wartość jest używana do określania, ile `CStringData` obiektów ciągów współużytkuje ten sam obiekt.

- Rzeczywisty bufor znaków ( [dane](#data)) ciągu.

   > [!NOTE]
   > Rzeczywisty bufor znaków obiektu ciągu jest przydzielany przez menedżera ciągów i dołączany do `CStringData` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr.h

## <a name="cstringdataaddref"></a><a name="addref"></a>CStringData::Odnośnik

Zwiększa liczbę odwołań obiektu ciągu.

```cpp
void AddRef() throw();
```

### <a name="remarks"></a>Uwagi

Zwiększa liczbę odwołań obiektu ciągu.

> [!NOTE]
> Nie należy wywoływać tej metody na ciąg z ujemną liczbą odwołań, ponieważ liczba ujemna wskazuje, że bufor ciągu jest zablokowany.

## <a name="cstringdatadata"></a><a name="data"></a>CStringData::data

Zwraca wskaźnik do buforu znaków obiektu ciągu.

```cpp
void* data() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu znaków obiektu ciągu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zwrócić bieżący bufor znaków skojarzonego obiektu ciągu.

> [!NOTE]
> Ten bufor nie jest `CStringData` przydzielany przez obiekt, ale przez menedżera ciągów w razie potrzeby. Po przydzieleniu bufor jest dołączany do obiektu danych ciągu.

## <a name="cstringdataislocked"></a><a name="islocked"></a>CStringData::Jest zablokowany

Określa, czy bufor znaków jest zablokowany.

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli bufor jest zablokowany; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby ustalić, czy bufor znaków obiektu ciągu jest obecnie zablokowany.

## <a name="cstringdataisshared"></a><a name="isshared"></a>CStringData::IsShared

Określa, czy bufor znaków jest współużytkowany.

```
bool IsShared() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli bufor jest współużytkowany; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby ustalić, czy bufor znaków obiektu danych ciągu jest obecnie współużytkowany przez wiele obiektów ciągów.

## <a name="cstringdatalock"></a><a name="lock"></a>CStringData::Zablokuj

Blokuje bufor znaków skojarzonego obiektu ciągu.

```cpp
void Lock() throw();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zablokować bufor znaków obiektu danych ciągu. Blokowanie i odblokowywanie jest używany, gdy bezpośredni dostęp do buforu znaków jest wymagane przez dewelopera. Dobrym przykładem blokowania jest wykazane przez [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) i `CSimpleStringT` [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metody .

> [!NOTE]
> Bufor znaków można zablokować tylko wtedy, gdy bufor nie jest współużytkowany przez obiekty wyższego ciągu.

## <a name="cstringdatanalloclength"></a><a name="nalloclength"></a>CStringData::nAllocLength

Długość przydzielonego buforu znaków.

```
int nAllocLength;
```

### <a name="remarks"></a>Uwagi

Przechowuje długość przydzielonego buforu danych w `XCHAR`s (nie łącznie z zakończeniem null).

## <a name="cstringdatandatalength"></a><a name="ndatalength"></a>CStringData::nDataLength

Bieżąca długość obiektu ciągu.

```
int nDataLength;
```

### <a name="remarks"></a>Uwagi

Przechowuje długość aktualnie używanych danych w `XCHAR`s (z wyłączeniem zakończenia null).

## <a name="cstringdatanrefs"></a><a name="nrefs"></a>CStringData::nRefs

Liczba odwołań obiektu danych ciągu.

```
long nRefs;
```

### <a name="remarks"></a>Uwagi

Przechowuje liczbę odwołań obiektu danych ciągu. Ta liczba wskazuje liczbę wyższych obiektów ciągu, które są skojarzone z obiektem danych ciągu. Wartość ujemna wskazuje, że obiekt danych ciągu jest obecnie zablokowany.

## <a name="cstringdatapstringmgr"></a><a name="pstringmgr"></a>CStringData::pStringMgr

Menedżer pamięci skojarzonego obiektu ciągu.

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>Uwagi

Przechowuje menedżera pamięci dla skojarzonego obiektu ciągu. Aby uzyskać więcej informacji na temat menedżerów pamięci i ciągów, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringdatarelease"></a><a name="release"></a>CStringData::Release

Zmniejsza liczbę odwołań obiektu danych ciągu.

```cpp
void Release() throw();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zniegoczyć `CStringData` liczbę odwołań, zwalniając strukturę, jeśli liczba odwołań osiągnie zero. Jest to często wykonywane po usunięciu obiektu ciągu i dlatego nie musi już odwoływać się do obiektu danych ciągu.

Na przykład następujący kod `CStringData::Release` wywoła obiekt danych ciągu `str1`skojarzony z:

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

## <a name="cstringdataunlock"></a><a name="unlock"></a>CStringData::Odblokuj

Odblokowuje bufor znaków skojarzonego obiektu ciągu.

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby odblokować bufor znaków obiektu danych ciągu. Po odblokowaniu buforu jest współużytkowany i można go zliczyć.

> [!NOTE]
> Każde wywołanie `Lock` musi być dopasowane przez `Unlock`odpowiednie wywołanie .

Blokowanie i odblokowywanie jest używane, gdy deweloper musi upewnić się, że dane ciągu nie są udostępniane. Dobrym przykładem blokowania jest wykazane przez [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) i `CSimpleStringT` [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metody .

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
