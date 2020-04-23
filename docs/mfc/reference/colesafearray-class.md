---
title: Klasa COleSafeArray
ms.date: 08/29/2019
f1_keywords:
- COleSafeArray
- AFXDISP/COleSafeArray
- AFXDISP/COleSafeArray::COleSafeArray
- AFXDISP/COleSafeArray::AccessData
- AFXDISP/COleSafeArray::AllocData
- AFXDISP/COleSafeArray::AllocDescriptor
- AFXDISP/COleSafeArray::Attach
- AFXDISP/COleSafeArray::Clear
- AFXDISP/COleSafeArray::Copy
- AFXDISP/COleSafeArray::Create
- AFXDISP/COleSafeArray::CreateOneDim
- AFXDISP/COleSafeArray::Destroy
- AFXDISP/COleSafeArray::DestroyData
- AFXDISP/COleSafeArray::DestroyDescriptor
- AFXDISP/COleSafeArray::Detach
- AFXDISP/COleSafeArray::GetByteArray
- AFXDISP/COleSafeArray::GetDim
- AFXDISP/COleSafeArray::GetElement
- AFXDISP/COleSafeArray::GetElemSize
- AFXDISP/COleSafeArray::GetLBound
- AFXDISP/COleSafeArray::GetOneDimSize
- AFXDISP/COleSafeArray::GetUBound
- AFXDISP/COleSafeArray::Lock
- AFXDISP/COleSafeArray::PtrOfIndex
- AFXDISP/COleSafeArray::PutElement
- AFXDISP/COleSafeArray::Redim
- AFXDISP/COleSafeArray::ResizeOneDim
- AFXDISP/COleSafeArray::UnaccessData
- AFXDISP/COleSafeArray::Unlock
helpviewer_keywords:
- COleSafeArray [MFC], COleSafeArray
- COleSafeArray [MFC], AccessData
- COleSafeArray [MFC], AllocData
- COleSafeArray [MFC], AllocDescriptor
- COleSafeArray [MFC], Attach
- COleSafeArray [MFC], Clear
- COleSafeArray [MFC], Copy
- COleSafeArray [MFC], Create
- COleSafeArray [MFC], CreateOneDim
- COleSafeArray [MFC], Destroy
- COleSafeArray [MFC], DestroyData
- COleSafeArray [MFC], DestroyDescriptor
- COleSafeArray [MFC], Detach
- COleSafeArray [MFC], GetByteArray
- COleSafeArray [MFC], GetDim
- COleSafeArray [MFC], GetElement
- COleSafeArray [MFC], GetElemSize
- COleSafeArray [MFC], GetLBound
- COleSafeArray [MFC], GetOneDimSize
- COleSafeArray [MFC], GetUBound
- COleSafeArray [MFC], Lock
- COleSafeArray [MFC], PtrOfIndex
- COleSafeArray [MFC], PutElement
- COleSafeArray [MFC], Redim
- COleSafeArray [MFC], ResizeOneDim
- COleSafeArray [MFC], UnaccessData
- COleSafeArray [MFC], Unlock
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
ms.openlocfilehash: 10e9975bac776429a38bfc707215a9465ce35c2e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753769"
---
# <a name="colesafearray-class"></a>Klasa COleSafeArray

Klasa do pracy z tablicami dowolnego typu i wymiaru.

## <a name="syntax"></a>Składnia

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|Konstruuje `COleSafeArray` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleSafeArray::AccessData](#accessdata)|Pobiera wskaźnik do danych tablicy.|
|[COleSafeArray::AllocData](#allocdata)|Przydziela pamięć dla tablicy.|
|[COleSafeArray::AllocDeptor](#allocdescriptor)|Przydziela pamięć dla deskryptora tablicy bezpiecznej.|
|[COleSafeArray::Dołącz](#attach)|Daje kontrolę nad `VARIANT` istniejącą `COleSafeArray` tablicą do obiektu.|
|[COleSafeArray::Wyczyść](#clear)|Zwalnia wszystkie dane w `VARIANT`podstawowej .|
|[COleSafeArray::Kopiowanie](#copy)|Tworzy kopię istniejącej tablicy.|
|[COleSafeArray::Tworzenie](#create)|Tworzy bezpieczną tablicę.|
|[COleSafeArray::CreateOneDim](#createonedim)|Tworzy `COleSafeArray` obiekt jednowymiarowy.|
|[COleSafeArray::Destroy](#destroy)|Niszczy istniejącą tablicę.|
|[COleSafeArray::DestroyData](#destroydata)|Niszczy dane w bezpiecznej tablicy.|
|[COleSafeArray::DestroyDeptor](#destroydescriptor)|Niszczy deskryptor bezpiecznej tablicy.|
|[COleSafeArray::Detach](#detach)|Odłącza tablicę VARIANT `COleSafeArray` od obiektu (tak, aby dane nie zostały zwolnione).|
|[COleSafeArray::GetByteArray](#getbytearray)|Kopiuje zawartość bezpiecznej tablicy do [CByteArray](../../mfc/reference/cbytearray-class.md).|
|[COleSafeArray::GetDim](#getdim)|Zwraca liczbę wymiarów w tablicy.|
|[COleSafeArray::GetElement](#getelement)|Pobiera pojedynczy element tablicy bezpieczne.|
|[COleSafeArray::GetElemSize](#getelemsize)|Zwraca rozmiar (w bajtach) jednego elementu w tablicy bezpiecznej.|
|[COleSafeArray::GetLBound](#getlbound)|Zwraca dolną granicę dla dowolnego wymiaru bezpiecznej tablicy.|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Zwraca liczbę elementów w `COleSafeArray` obiekcie jednowymiarowym.|
|[COleSafeArray::GetUBound](#getubound)|Zwraca górną granicę dla dowolnego wymiaru bezpiecznej tablicy.|
|[COleSafeArray::Blokada](#lock)|Zwiększa liczbę blokad tablicy i umieszcza wskaźnik do danych tablicy w deskryptorze tablicy.|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Zwraca wskaźnik do elementu indeksowanego.|
|[COleSafeArray::PutElement](#putelement)|Przypisuje pojedynczy element do tablicy.|
|[COleSafeArray::Redim](#redim)|Zmienia najmniej istotne (po prawej) związane z bezpiecznej tablicy.|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Zmienia liczbę elementów w `COleSafeArray` obiekcie jednowymiarowym.|
|[COleSafeArray::UnaccessData](#unaccessdata)|Zmniejsza liczbę blokad tablicy i unieważnia wskaźnik pobrany przez `AccessData`program .|
|[COleSafeArray::Odblokuj](#unlock)|Zmniejsza liczbę blokad tablicy, dzięki czemu można ją zwolniono lub zmieścić.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|Uzyskuje dostęp `VARIANT` do podstawowej struktury `COleSafeArray` obiektu.|
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|Uzyskuje dostęp `VARIANT` do podstawowej struktury `COleSafeArray` obiektu.|
|[COleSafeArray::operator =](#operator_eq)|Kopiuje wartości `COleSafeArray` do`SAFEARRAY` `VARIANT`obiektu `COleVariant`( `COleSafeArray` , , , lub tablicy).|
|[COleSafeArray::operator ==](#operator_eq_eq)|Porównuje dwie tablice`SAFEARRAY`wariantowe `COleVariant`( `COleSafeArray` , `VARIANT`, , lub tablice).|
|[COleSafeArray::operator&lt;&lt;](#operator_lt_lt)|Wyprowadza zawartość `COleSafeArray` obiektu do kontekstu zrzutu.|

## <a name="remarks"></a>Uwagi

`COleSafeArray`pochodzi ze struktury `VARIANT` OLE. Funkcje `SAFEARRAY` elementów członkowskich `COleSafeArray`OLE są dostępne za pośrednictwem , a także zestaw funkcji członkowskich specjalnie zaprojektowany dla jednowymiarowych tablic bajtów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="colesafearrayaccessdata"></a><a name="accessdata"></a>COleSafeArray::AccessData

Pobiera wskaźnik do danych tablicy.

```cpp
void AccessData(void** ppvData);
```

### <a name="parameters"></a>Parametry

*ppvData (dane z punktu/*<br/>
Wskaźnik do wskaźnika do danych tablicy.

### <a name="remarks"></a>Uwagi

Na błąd, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

## <a name="colesafearrayallocdata"></a><a name="allocdata"></a>COleSafeArray::AllocData

Przydziela pamięć dla bezpiecznej tablicy.

```cpp
void AllocData();
```

### <a name="remarks"></a>Uwagi

Na błąd, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayallocdescriptor"></a><a name="allocdescriptor"></a>COleSafeArray::AllocDeptor

Przydziela pamięć dla deskryptora bezpiecznej tablicy.

```cpp
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>Parametry

*dwDims ( dwDims )*<br/>
Liczba wymiarów w tablicy bezpiecznej.

### <a name="remarks"></a>Uwagi

Na błąd, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayattach"></a><a name="attach"></a>COleSafeArray::Dołącz

Daje kontrolę nad danymi `VARIANT` w istniejącej tablicy `COleSafeArray` do obiektu.

```cpp
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parametry

*varSrc ( varSrc )*<br/>
Obiekt `VARIANT`. Parametr *varSrc* musi mieć [VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum)VARTYPE .

### <a name="remarks"></a>Uwagi

Typ `VARIANT`źródła jest ustawiony na VT_EMPTY. Ta funkcja czyści bieżące dane tablicy, jeśli istnieją.

### <a name="example"></a>Przykład

  Zobacz przykład [dla COleSafeArray::AccessData](#accessdata).

## <a name="colesafearrayclear"></a><a name="clear"></a>COleSafeArray::Wyczyść

Czyści bezpieczną tablicę.

```cpp
void Clear();
```

### <a name="remarks"></a>Uwagi

Funkcja czyści bezpieczną tablicę, `VARTYPE` ustawiając obiekt na VT_EMPTY. Bieżąca zawartość są zwalniane i tablica jest zwalniana.

## <a name="colesafearraycolesafearray"></a><a name="colesafearray"></a>COleSafeArray::COleSafeArray

Konstruuje `COleSafeArray` obiekt.

```
COleSafeArray();

COleSafeArray(
    const SAFEARRAY& saSrc,
    VARTYPE vtSrc);

COleSafeArray(
    LPCSAFEARRAY pSrc,
    VARTYPE vtSrc);

COleSafeArray(const COleSafeArray& saSrc);
COleSafeArray(const VARIANT& varSrc);
COleSafeArray(LPCVARIANT pSrc);
COleSafeArray(const COleVariant& varSrc);
```

### <a name="parameters"></a>Parametry

*saSrc ( saSrc )*<br/>
Istniejący `COleSafeArray` obiekt `SAFEARRAY` lub do skopiowania `COleSafeArray` do nowego obiektu.

*Vtsrc*<br/>
Typ VARTYPE nowego `COleSafeArray` obiektu.

*psaSrc (psaSrc)*<br/>
Wskaźnik do `SAFEARRAY` a do skopiowania `COleSafeArray` do nowego obiektu.

*varSrc ( varSrc )*<br/>
Istniejący `VARIANT` `COleVariant` lub obiekt do skopiowania `COleSafeArray` do nowego obiektu.

*Psrc*<br/>
Wskaźnik do `VARIANT` obiektu, który ma zostać `COleSafeArray` skopiowany do nowego obiektu.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory tworzą nowe `COleSafeArray` obiekty. Jeśli nie ma parametru, tworzony jest pusty `COleSafeArray` obiekt (VT_EMPTY). Jeśli `COleSafeArray` jest kopiowany z innej tablicy, której `COleSafeArray`VARTYPE jest znany niejawnie (a , `COleVariant`, lub `VARIANT`), VARTYPE tablicy źródłowej jest zachowywany i nie musi być określony. Jeśli `COleSafeArray` jest kopiowany z innej tablicy,`SAFEARRAY`której VARTYPE nie jest znany ( ), vartype musi być określony w *vtSrc* parametru.

Na błąd, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraycopy"></a><a name="copy"></a>COleSafeArray::Kopiowanie

Tworzy kopię istniejącej bezpiecznej tablicy.

```cpp
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>Parametry

*ppsa*<br/>
Wskaźnik do lokalizacji, w której ma być zwracany nowy deskryptor tablicy.

### <a name="remarks"></a>Uwagi

Na błąd, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraycreate"></a><a name="create"></a>COleSafeArray::Tworzenie

Przydziela i inicjuje dane dla tablicy.

```cpp
void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    DWORD* rgElements);

void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    SAFEARRAYBOUND* rgsabounds);
```

### <a name="parameters"></a>Parametry

*Vtsrc*<br/>
Typ podstawowy tablicy (czyli VARTYPE każdego elementu tablicy). VARTYPE jest ograniczona do podzbioru typów wariantów. Nie można ustawić ani VT_ARRAY, ani flagi VT_BYREF. VT_EMPTY i VT_NULL nie są prawidłowe typy podstawowe dla tablicy. Wszystkie inne typy są legalne.

*dwDims ( dwDims )*<br/>
Liczba wymiarów w tablicy. Można to zmienić po utworzeniu tablicy za pomocą [redim](#redim).

*rgElements (Polski)*<br/>
Wskaźnik do tablicy liczby elementów dla każdego wymiaru w tablicy.

*rgsabounds (rgsabounds)*<br/>
Wskaźnik do wektora granic (po jednym dla każdego wymiaru), aby przydzielić dla tablicy.

### <a name="remarks"></a>Uwagi

Ta funkcja wyczyści bieżące dane tablicy, jeśli to konieczne. Na błąd, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraycreateonedim"></a><a name="createonedim"></a>COleSafeArray::CreateOneDim

Tworzy nowy `COleSafeArray` obiekt jednowymiarowy.

```cpp
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>Parametry

*Vtsrc*<br/>
Typ podstawowy tablicy (czyli VARTYPE każdego elementu tablicy).

*dwElements*<br/>
Liczba elementów w tablicy. Można to zmienić po utworzeniu tablicy za pomocą [pliku ResizeOneDim](#resizeonedim).

*pvSrcData*<br/>
Wskaźnik do danych do skopiowania do tablicy.

*nLBound (Przylot)*<br/>
Dolna granica tablicy.

### <a name="remarks"></a>Uwagi

Funkcja przydziela i inicjuje dane dla tablicy, kopiując określone dane, jeśli wskaźnik *pvSrcData* nie ma wartości NULL.

Na błąd, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

## <a name="colesafearraydestroy"></a><a name="destroy"></a>COleSafeArray::Destroy

Niszczy istniejący deskryptor tablicy i wszystkie dane w tablicy.

```cpp
void Destroy();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekty są przechowywane w tablicy, każdy obiekt jest zwolniony. Na błąd, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydestroydata"></a><a name="destroydata"></a>COleSafeArray::DestroyData

Niszczy wszystkie dane w bezpiecznej tablicy.

```cpp
void DestroyData();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekty są przechowywane w tablicy, każdy obiekt jest zwolniony. Na błąd, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydestroydescriptor"></a><a name="destroydescriptor"></a>COleSafeArray::DestroyDeptor

Niszczy deskryptor bezpiecznej tablicy.

```cpp
void DestroyDescriptor();
```

### <a name="remarks"></a>Uwagi

Na błąd, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearraydetach"></a><a name="detach"></a>COleSafeArray::Detach

Odłącza `VARIANT` dane od `COleSafeArray` obiektu.

```
VARIANT Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wartość `VARIANT` podstawowa `COleSafeArray` w obiekcie.

### <a name="remarks"></a>Uwagi

Funkcja odłącza dane w bezpiecznej tablicy, ustawiając vartype obiektu na VT_EMPTY. Jest to odpowiedzialność dzwoniącego, aby zwolnić tablicy, wywołując funkcję Systemu Windows [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear).

Na błąd, funkcja rzuca [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

  Zobacz przykład [dla COleSafeArray::PutElement](#putelement).

## <a name="colesafearraygetbytearray"></a><a name="getbytearray"></a>COleSafeArray::GetByteArray

Kopiuje zawartość tablicy bezpiecznej do pliku `CByteArray`.

```cpp
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parametry

*Bajtów*<br/>
Odwołanie do [obiektu CByteArray.](../../mfc/reference/cbytearray-class.md)

## <a name="colesafearraygetdim"></a><a name="getdim"></a>COleSafeArray::GetDim

Zwraca liczbę wymiarów `COleSafeArray` w obiekcie.

```
DWORD GetDim();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wymiarów w tablicy bezpiecznej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraygetelement"></a><a name="getelement"></a>COleSafeArray::GetElement

Pobiera pojedynczy element tablicy bezpieczne.

```cpp
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parametry

*rgIndices (rgIndices)*<br/>
Wskaźnik do tablicy indeksów dla każdego wymiaru tablicy.

*pvDana*<br/>
Wskaźnik do lokalizacji, aby umieścić element tablicy.

### <a name="remarks"></a>Uwagi

Ta funkcja automatycznie wywołuje `SafeArrayLock` funkcje systemu Windows oraz `SafeArrayUnlock` przed i po pobraniu elementu. Jeśli element danych jest ciągiem, obiektem lub wariantem, funkcja kopiuje element w prawidłowy sposób. Parametr *pvData* należy wskazać wystarczająco duży bufor, aby zawierać element.

Na błąd, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

## <a name="colesafearraygetelemsize"></a><a name="getelemsize"></a>COleSafeArray::GetElemSize

Pobiera rozmiar elementu w obiekcie. `COleSafeArray`

```
DWORD GetElemSize();
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar w bajtach elementów bezpiecznej tablicy.

## <a name="colesafearraygetlbound"></a><a name="getlbound"></a>COleSafeArray::GetLBound

Zwraca dolną granicę dla `COleSafeArray` dowolnego wymiaru obiektu.

```cpp
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>Parametry

*dwDim ( dwDim )*<br/>
Wymiar tablicy, dla którego ma zostać świązany dolna granica.

*pLBound (Przylot)*<br/>
Wskaźnik do lokalizacji, aby zwrócić dolną granicę.

### <a name="remarks"></a>Uwagi

Na błąd, funkcja rzuca [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

## <a name="colesafearraygetonedimsize"></a><a name="getonedimsize"></a>COleSafeArray::GetOneDimSize

Zwraca liczbę elementów w `COleSafeArray` obiekcie jednowymiarowym.

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy jednowymiarowej bezpiecznej.

### <a name="example"></a>Przykład

  Zobacz przykład [dla COleSafeArray::CreateOneDim](#createonedim).

## <a name="colesafearraygetubound"></a><a name="getubound"></a>COleSafeArray::GetUBound

Zwraca górną granicę dla dowolnego wymiaru bezpiecznej tablicy.

```cpp
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>Parametry

*dwDim ( dwDim )*<br/>
Wymiar tablicy, dla którego ma zostać śwolta górna.

*pUBound*<br/>
Wskaźnik do lokalizacji, aby zwrócić górną granicę.

### <a name="remarks"></a>Uwagi

Na błąd, funkcja rzuca [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

## <a name="colesafearraylock"></a><a name="lock"></a>COleSafeArray::Blokada

Zwiększa liczbę blokad tablicy i umieszcza wskaźnik danych tablicy w deskryptorze tablicy.

```cpp
void Lock();
```

### <a name="remarks"></a>Uwagi

Na błąd, rzuca [COleException](../../mfc/reference/coleexception-class.md).

Wskaźnik w deskryptorze tablicy jest prawidłowy, dopóki nie `Unlock` zostanie wywołany. Wywołania `Lock` mogą być zagnieżdżone; wymagana jest taka `Unlock` sama liczba połączeń.

Tablicy nie można usunąć, gdy jest zablokowana.

## <a name="colesafearrayoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleSafeArray::operator LPCVARIANT

Wywołanie tego operatora rzutowania, aby uzyskać dostęp do podstawowej `VARIANT` struktury dla tego `COleSafeArray` obiektu.

```
operator LPCVARIANT() const;
```

## <a name="colesafearrayoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleSafeArray::operator LPVARIANT

Wywołanie tego operatora rzutowania, aby uzyskać dostęp do podstawowej `VARIANT` struktury dla tego `COleSafeArray` obiektu.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Uwagi

Należy zauważyć, że `VARIANT` zmiana wartości w strukturze dostępne przez wskaźnik zwracany `COleSafeArray` przez tę funkcję spowoduje zmianę wartości tego obiektu.

## <a name="colesafearrayoperator-"></a><a name="operator_eq"></a>COleSafeArray::operator =

Te przeciążonych operatorów przypisania `COleSafeArray` skopiować wartość źródłową do tego obiektu.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Uwagi

Krótki opis każdego operatora jest następujący:

- **operator =(** *saSrc* **)** Kopiuje `COleSafeArray` istniejący obiekt do tego obiektu.

- **operator =(** *varSrc* **)** Kopiuje `VARIANT` istniejącą lub `COleVariant` tablicę do tego obiektu.

- **operator =(** *pSrc* **)** Kopiuje `VARIANT` obiekt tablicy, do który pSrc uzyskuje dostęp *pSrc,* do tego obiektu.

## <a name="colesafearrayoperator-"></a><a name="operator_eq_eq"></a>COleSafeArray::operator ==

Ten operator porównuje dwie`SAFEARRAY`tablice `COleVariant`( `COleSafeArray` , `VARIANT`, , lub tablice) i zwraca niezerowy, jeśli są równe; w przeciwnym razie 0.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Uwagi

Dwie tablice są równe, jeśli mają taką samą liczbę wymiarów, równy rozmiar w każdym wymiarze i równe wartości elementu.

## <a name="colesafearrayoperator-ltlt"></a><a name="operator_lt_lt"></a>COleSafeArray::operator&lt;&lt;

Operator `COleSafeArray` wstawiania (<<) obsługuje diagnostykę `COleSafeArray` dumpingu i przechowywania obiektu w archiwum.

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

## <a name="colesafearrayptrofindex"></a><a name="ptrofindex"></a>COleSafeArray::PtrOfIndex

Zwraca wskaźnik do elementu określonego przez wartości indeksu.

```cpp
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>Parametry

*rgIndices (rgIndices)*<br/>
Tablica wartości indeksu, które identyfikują element tablicy. Wszystkie indeksy dla elementu muszą być określone.

*ppvData (dane z punktu/*<br/>
Po zwrocie wskaźnik do elementu identyfikowane przez wartości w *rgIndices*.

## <a name="colesafearrayputelement"></a><a name="putelement"></a>COleSafeArray::PutElement

Przypisuje pojedynczy element do tablicy.

```cpp
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parametry

*rgIndices (rgIndices)*<br/>
Wskaźnik do tablicy indeksów dla każdego wymiaru tablicy.

*pvDana*<br/>
Wskaźnik do danych, które mają być przypisane do tablicy. VT_DISPATCH, VT_UNKNOWN i VT_BSTR typy wariantów są wskaźnikami i nie wymagają innego poziomu pośredniego.

### <a name="remarks"></a>Uwagi

Ta funkcja automatycznie wywołuje funkcje systemu Windows [SafeArrayLock](/windows/win32/api/oleauto/nf-oleauto-safearraylock) i [SafeArrayUnlock](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock) przed i po przypisaniu elementu. Jeśli element danych jest ciągiem, obiektem lub wariantem, funkcja kopiuje go poprawnie, a istniejący element jest ciągiem, obiektem lub wariantem, jest on poprawnie wyczyszczony.

Należy zauważyć, że może mieć wiele blokad na tablicy, dzięki czemu można umieścić elementy w tablicy, gdy tablica jest zablokowana przez inne operacje.

Na błąd, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

## <a name="colesafearrayredim"></a><a name="redim"></a>COleSafeArray::Redim

Zmienia najmniej istotne (po prawej) związane z bezpiecznej tablicy.

```cpp
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>Parametry

*psaboundNowy*<br/>
Wskaźnik do nowej bezpiecznej struktury związane tablicy zawierające nowe tablicy związane. Tylko najmniej znaczący wymiar tablicy mogą zostać zmienione.

### <a name="remarks"></a>Uwagi

Na błąd, funkcja rzuca [COleException](../../mfc/reference/coleexception-class.md).

## <a name="colesafearrayresizeonedim"></a><a name="resizeonedim"></a>COleSafeArray::ResizeOneDim

Zmienia liczbę elementów w `COleSafeArray` obiekcie jednowymiarowym.

```cpp
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>Parametry

*dwElements*<br/>
Liczba elementów w tablicy bezpieczeństwa jednowymiarowego.

### <a name="remarks"></a>Uwagi

Na błąd, funkcja rzuca [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

  Zobacz przykład [dla COleSafeArray::CreateOneDim](#createonedim).

## <a name="colesafearrayunaccessdata"></a><a name="unaccessdata"></a>COleSafeArray::UnaccessData

Zmniejsza liczbę blokad tablicy i unieważnia wskaźnik pobrany przez `AccessData`program .

```cpp
void UnaccessData();
```

### <a name="remarks"></a>Uwagi

Na błąd, funkcja rzuca [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

  Zobacz przykład [dla COleSafeArray::AccessData](#accessdata).

## <a name="colesafearrayunlock"></a><a name="unlock"></a>COleSafeArray::Odblokuj

Zmniejsza liczbę blokad tablicy, dzięki czemu można ją zwolniono lub zmieścić.

```cpp
void Unlock();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana po zakończeniu dostępu do danych w tablicy. Na błąd, rzuca [COleException](../../mfc/reference/coleexception-class.md).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleVariant](../../mfc/reference/colevariant-class.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
