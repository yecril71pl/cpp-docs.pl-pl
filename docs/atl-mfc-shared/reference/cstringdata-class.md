---
title: CStringData, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: effc4166fa25cec03ea62a5dd35a5396d2d2a3f2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419792"
---
# <a name="cstringdata-class"></a>CStringData, klasa

Ta klasa reprezentuje dane obiektu string.

## <a name="syntax"></a>Składnia

```
struct CStringData
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[AddRef](#addref)|Zwiększa licznik odwołań obiektu danych ciągu.|
|[Dane](#data)|Pobiera dane znaków obiektu ciągu.|
|[IsLocked](#islocked)|Określa, jeśli bufor z obiektem ciągu skojarzone jest zablokowany.|
|[IsShared](#isshared)|Określa, jeśli bufor z obiektem ciągu skojarzone jest obecnie udostępniana.|
|[Blokady](#lock)|Blokuje buforu ciągu skojarzonego obiektu.|
|[Wersja](#release)|Zwalnia obiektu określonego ciągu.|
|[Odblokowywanie](#unlock)|Odblokowuje buforu ciągu skojarzonego obiektu.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[nAllocLength](#nalloclength)|Długość danych przydzielone w `XCHAR`s (bez uwzględniania zakończenia o wartości null)|
|[nDataLength](#ndatalength)|Długość danych aktualnie używanego w `XCHAR`s (bez uwzględniania zakończenia o wartości null)|
|[nRefs](#nrefs)|Bieżąca liczba odwołań obiektu.|
|[pStringMgr](#pstringmgr)|Wskaźnik do Menedżera ciągów tego obiektu ciągu.|

## <a name="remarks"></a>Uwagi

Ta klasa powinna wykorzystywane przez deweloperów, implementowanie menedżerów niestandardowy ciąg. Aby uzyskać więcej informacji na temat niestandardowy ciąg menedżerów, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

Ta klasa hermetyzuje różnego rodzaju informacje i dane związane z obiektem ciągu wyższe, takie jak [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), lub [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) obiekty. Każdy wyższe obiekt ciągu zawiera wskaźnik do związanych z nią `CStringData` obiektu, dzięki czemu wiele obiektów ciągu wskazywały ten sam obiekt ciąg w danych. Ta relacja jest reprezentowany przez licznik odwołań (`nRefs`) z `CStringData` obiektu.

> [!NOTE]
>  W niektórych przypadkach typu string (takie jak `CFixedString`) nie współużytkują obiekt danych ciągu z więcej niż jeden obiekt ciągu wyższy. Aby uzyskać więcej informacji na temat tego, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

Te dane składa się z:

- Menedżer pamięci (typu [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) ciągu.

- Bieżąca długość ( [nDataLength](#ndatalength)) ciągu.

- Przydzielone długość ( [nAllocLength](#nalloclength)) ciągu. Ze względu na wydajność to może być inna niż bieżąca długość ciągu

- Bieżąca liczba odwołań ( [nRefs](#nrefs)) z `CStringData` obiektu. Ta wartość jest używana w określeniu, jak wiele obiektów w postaci ciągów, którzy udostępniają takie same `CStringData` obiektu.

- Bufor znak, który faktycznie ( [danych](#data)) ciągu.

   > [!NOTE]
   > Bufor znak, który faktycznie z obiektem ciągu jest przydzielany przez Menedżera ciągów i jest dołączany do `CStringData` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr.h

##  <a name="addref"></a>  CStringData::AddRef

Zwiększa licznik odwołań obiektu ciągu.

```
void AddRef() throw();
```

### <a name="remarks"></a>Uwagi

Zwiększa licznik odwołań obiektu ciągu.

> [!NOTE]
>  Nie wywołać tę metodę w ciągu z liczbą ujemną odwołanie, ponieważ liczba ujemna oznacza, że buforu ciągu jest zablokowany.

##  <a name="data"></a>  CStringData::data

Zwraca wskaźnik do buforu znaku obiektu ciągu.

```
void* data() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu znaków ciągu obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby powrócić do bieżącego buforu znaku w ciągu skojarzonego obiektu.

> [!NOTE]
>  Ten bufor nie jest przydzielany przez `CStringData` obiektu, ale przez Menedżera ciągów, w razie. Przydzielone, rozmiar buforu jest dołączany do ciągu obiektu danych.

##  <a name="islocked"></a>  CStringData::IsLocked

Określa, jeśli jest zablokowana buforu znaków.

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli bufor jest zablokowany; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby określić, jeśli bufor znaków obiekt ciągu jest obecnie zablokowany.

##  <a name="isshared"></a>  CStringData::IsShared

Określa, jeśli jest udostępniana buforu znaków.

```
bool IsShared() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli bufor jest udostępniony; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby określić, jeśli bufor znaków obiektu ciągu danych obecnie jest współużytkowana przez wiele obiektów w postaci ciągów.

##  <a name="lock"></a>  CStringData::Lock

Blokuje buforu znaków ciągu skojarzonego obiektu.

```
void Lock() throw();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję do blokowania bufora znaków ciągu obiektu danych. Blokowanie i odblokowywanie jest używany, gdy bezpośredni dostęp do buforu znaków jest wymagany przez dewelopera. Dobrym przykładem blokowania obrazuje [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) i [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metody `CSimpleStringT`.

> [!NOTE]
>  Bufor znaków może być zablokowany, jeśli bufor nie jest współużytkowana przez wyższe obiektów w postaci ciągów.

##  <a name="nalloclength"></a>  CStringData::nAllocLength

Długość buforu przydzielone znaków.

```
int nAllocLength;
```

### <a name="remarks"></a>Uwagi

Przechowuje długość buforu przydzielone dane w `XCHAR`s (bez uwzględniania zakończenia o wartości null).

##  <a name="ndatalength"></a>  CStringData::nDataLength

Bieżąca długość z obiektem ciągu.

```
int nDataLength;
```

### <a name="remarks"></a>Uwagi

Przechowuje długość danych aktualnie używanego w `XCHAR`s (bez uwzględniania zakończenia o wartości null).

##  <a name="nrefs"></a>  CStringData::nRefs

Licznik odwołań obiektu danych ciągu.

```
long nRefs;
```

### <a name="remarks"></a>Uwagi

Przechowuje licznik odwołań obiektu danych ciągu. Ten licznik wskazuje liczbę wyższe obiektów ciągu, które są skojarzone z obiektem ciągu danych. Ujemna wartość oznacza obiekt ciągu danych jest obecnie zablokowany.

##  <a name="pstringmgr"></a>  CStringData::pStringMgr

Menedżer pamięci obiektu skojarzone parametry.

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>Uwagi

Przechowuje Menedżer pamięci dla obiektu skojarzonego ciągu. Aby uzyskać więcej informacji na temat menedżerów zarządzania pamięcią i ciągi, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="release"></a>  CStringData::Release

Dekrementuje liczbę odwołań dla obiektu danych ciągu.

```
void Release() throw();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zmniejszyć liczbę odwołań zwalnianie `CStringData` struktury, jeśli liczba odwołań osiąga zero. Odbywa się często, gdy obiekt ciągu, który zostanie usunięty, a w związku z tym nie jest już musi odwoływać się do obiektu danych ciągu.

Na przykład, poniższy kod wywoływałby `CStringData::Release` dla obiektu danych ciągu związanych z `str1`:

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

##  <a name="unlock"></a>  CStringData::Unlock

Odblokowuje buforu znaków ciągu skojarzonego obiektu.

```
void Unlock() throw();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby odblokować buforu znaków ciągu obiektu danych. Po odblokowaniu bufor jest możliwa do udostępniania i może być odwołania liczony.

> [!NOTE]
>  Każde wywołanie `Lock` musi towarzyszyć do odpowiedniego wywołania `Unlock`.

Blokowanie i odblokowywanie jest używany, gdy deweloper należy upewnić się, że dane ciągu nie można udostępnić. Dobrym przykładem blokowania obrazuje [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) i [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metody `CSimpleStringT`.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)

