---
title: COleSafeArray Class
ms.date: 08/27/2018
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
ms.openlocfilehash: 0833dca9311689063c2ebeadd3942d9f5ce376e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224426"
---
# <a name="colesafearray-class"></a>COleSafeArray Class

Klasa pracy z tablicami dowolnego typu i wymiar.

## <a name="syntax"></a>Składnia

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|Konstruuje `COleSafeArray` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleSafeArray::AccessData](#accessdata)|Pobiera wskaźnik do danych tablicy.|
|[COleSafeArray::AllocData](#allocdata)|Przydziela pamięć dla tablicy.|
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Przydziela pamięć dla deskryptora bezpieczną tablicą.|
|[COleSafeArray::Attach](#attach)|Zapewnia kontrolę nad istniejące `VARIANT` tablicy do `COleSafeArray` obiektu.|
|[COleSafeArray::Clear](#clear)|Zwalnia wszystkie dane w źródłowym `VARIANT`.|
|[COleSafeArray::Copy](#copy)|Tworzy kopię istniejącej tablicy.|
|[COleSafeArray::Create](#create)|Tworzy bezpieczną tablicą.|
|[COleSafeArray::CreateOneDim](#createonedim)|Tworzy jednowymiarową `COleSafeArray` obiektu.|
|[COleSafeArray::Destroy](#destroy)|Niszczy istniejącej tablicy.|
|[COleSafeArray::DestroyData](#destroydata)|Niszczy dane w bezpiecznej tablicy.|
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Niszczy deskryptor bezpieczną tablicą.|
|[COleSafeArray::Detach](#detach)|Odłącza tablica wariant `COleSafeArray` obiektu (tak, aby dane nie zostanie zwolniona,).|
|[COleSafeArray::GetByteArray](#getbytearray)|Kopiuje zawartość do bezpiecznej tablicy do [CByteArray](../../mfc/reference/cbytearray-class.md).|
|[COleSafeArray::GetDim](#getdim)|Zwraca liczbę wymiarów w tablicy.|
|[COleSafeArray::GetElement](#getelement)|Pobiera pojedynczy element bezpieczną tablicą.|
|[COleSafeArray::GetElemSize](#getelemsize)|Zwraca rozmiar w bajtach, jeden element w tablicy bezpieczne.|
|[COleSafeArray::GetLBound](#getlbound)|Zwraca dolną granicę dla każdego wymiaru tablicy bezpiecznej.|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Zwraca liczbę elementów w jednowymiarowy `COleSafeArray` obiektu.|
|[COleSafeArray::GetUBound](#getubound)|Zwraca górną granicę dla każdego wymiaru tablicy bezpiecznej.|
|[COleSafeArray::Lock](#lock)|Zwiększa liczbę blokad tablicy, a następnie umieszcza wskaźnik do danych w deskryptora tablicy.|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Zwraca wskaźnik do elementu indeksowanego.|
|[COleSafeArray::PutElement](#putelement)|Przypisuje jeden element w tablicy.|
|[COleSafeArray::Redim](#redim)|Zmienia najmniej znaczący (po prawej stronie) granicę bezpiecznej tablicy.|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Zmienia liczbę elementów w jednowymiarowym `COleSafeArray` obiektu.|
|[COleSafeArray::UnaccessData](#unaccessdata)|Dekrementuje blokada count tablicę i unieważnia wskaźnika pobierane przez `AccessData`.|
|[COleSafeArray::Unlock](#unlock)|Zmniejsza liczbę blokad tablicy, może być zwolniona lub zmiany rozmiaru.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|Uzyskuje dostęp do podstawowych `VARIANT` struktury `COleSafeArray` obiektu.|
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|Uzyskuje dostęp do podstawowych `VARIANT` struktury `COleSafeArray` obiektu.|
|[COleSafeArray::operator =](#operator_eq)|Kopiuje wartości do `COleSafeArray` obiektu (`SAFEARRAY`, `VARIANT`, `COleVariant`, lub `COleSafeArray` tablicy).|
|[COleSafeArray::operator ==](#operator_eq_eq)|Porównuje dwie tablice variant (`SAFEARRAY`, `VARIANT`, `COleVariant`, lub `COleSafeArray` tablicami).|
|[COleSafeArray::operator &lt;&lt;](#operator_lt_lt)|Wyświetla zawartość `COleSafeArray` obiektu kontekstu zrzutu.|

## <a name="remarks"></a>Uwagi

`COleSafeArray` pochodzi z OLE `VARIANT` struktury. OLE `SAFEARRAY` funkcje składowe są dostępne za pośrednictwem `COleSafeArray`, jak również jako zestaw elementów członkowskich zaprojektowane specjalnie dla tablic jednowymiarowych bajtów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

##  <a name="accessdata"></a>  COleSafeArray::AccessData

Pobiera wskaźnik do danych tablicy.

```
void AccessData(void** ppvData);
```

### <a name="parameters"></a>Parametry

*ppvData*<br/>
Wskaźnik do wskaźnika do tablicy danych.

### <a name="remarks"></a>Uwagi

W przypadku błędu, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

##  <a name="allocdata"></a>  COleSafeArray::AllocData

Przydziela pamięć dla bezpiecznej tablicy.

```
void AllocData();
```

### <a name="remarks"></a>Uwagi

W przypadku błędu, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="allocdescriptor"></a>  COleSafeArray::AllocDescriptor

Przydziela pamięć dla deskryptora bezpieczną tablicą.

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>Parametry

*dwDims*<br/>
Liczba wymiarów w bezpiecznej tablicy.

### <a name="remarks"></a>Uwagi

W przypadku błędu, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="attach"></a>  COleSafeArray::Attach

Zapewnia kontrolę nad danymi w istniejącym `VARIANT` tablicy do `COleSafeArray` obiektu.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
Element `VARIANT` obiektu. *VarSrc* parametr musi mieć VARTYPE [VT_ARRAY](/windows/desktop/api/wtypes/ne-wtypes-varenum).

### <a name="remarks"></a>Uwagi

Źródło `VARIANT`tego typu jest ustawiona na VT_EMPTY. Tę funkcję, czyści bieżące dane tablicy, jeśli istnieje.

### <a name="example"></a>Przykład

  Zobacz przykład [COleSafeArray::AccessData](#accessdata).

##  <a name="clear"></a>  COleSafeArray::Clear

Czyści bezpieczną tablicą.

```
void Clear();
```

### <a name="remarks"></a>Uwagi

Funkcja czyści bezpieczną tablicą, ustawiając `VARTYPE` obiektu VT_EMPTY. Bieżącą zawartość zostaną zwolnione i tablicy jest zwalniana.

##  <a name="colesafearray"></a>  COleSafeArray::COleSafeArray

Konstruuje `COleSafeArray` obiektu.

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

*saSrc*<br/>
Istniejące `COleSafeArray` obiektu lub `SAFEARRAY` do skopiowania w nowe `COleSafeArray` obiektu.

*vtSrc*<br/>
VARTYPE nowej `COleSafeArray` obiektu.

*psaSrc*<br/>
Wskaźnik do `SAFEARRAY` do skopiowania w nowe `COleSafeArray` obiektu.

*varSrc*<br/>
Istniejące `VARIANT` lub `COleVariant` obiektu do skopiowania w nowe `COleSafeArray` obiektu.

*pSrc*<br/>
Wskaźnik do `VARIANT` obiektu do skopiowania w nowe `COleSafeArray` obiektu.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory tworzą nowe `COleSafeArray` obiektów. Jeśli nie ma parametru, pusta `COleSafeArray` obiekt zostanie utworzony (VT_EMPTY). Jeśli `COleSafeArray` jest kopiowany z innej tablicy, w których VARTYPE jest niejawnie określany ( `COleSafeArray`, `COleVariant`, lub `VARIANT`), VARTYPE tablicy źródłowej są zachowywane i nie musi być określony. Jeśli `COleSafeArray` jest kopiowany z innej tablicy, w których VARTYPE jest nieznany (`SAFEARRAY`), VARTYPE musi być określona w *vtSrc* parametru.

W przypadku błędu, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="copy"></a>  COleSafeArray::Copy

Tworzy kopię istniejącej bezpiecznej tablicy.

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>Parametry

*ppsa*<br/>
Wskaźnik do lokalizacji, w której ma zostać zwrócone nowego deskryptora tablicy.

### <a name="remarks"></a>Uwagi

W przypadku błędu, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="create"></a>  COleSafeArray::Create

Przydziela i inicjuje danych tablicy.

```
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

*vtSrc*<br/>
Typ bazowy tablicy (czyli VARTYPE każdego elementu tablicy). VARTYPE jest ograniczona do podzbioru typów variant. Można ustawić flagi VT_BYREF ani VT_ARRAY. VT_EMPTY i VT_NULL nie są prawidłowe typy podstawowe dla tablicy. Wszystkie inne typy są dozwolone.

*dwDims*<br/>
Liczba wymiarów w tablicy. Można go zmienić po utworzeniu tablicy [Redim](#redim).

*rgElements*<br/>
Wskaźnik do tablicy liczbę elementów w tablicy dla każdego wymiaru.

*rgsabounds*<br/>
Wskaźnik do wektora granic (po jednym dla każdego wymiaru) do przydzielenia dla tablicy.

### <a name="remarks"></a>Uwagi

Ta funkcja spowoduje wyczyszczenie bieżące dane tablicy, jeśli to konieczne. W przypadku błędu, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="createonedim"></a>  COleSafeArray::CreateOneDim

Tworzy nową jednowymiarowa `COleSafeArray` obiektu.

```
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>Parametry

*vtSrc*<br/>
Typ bazowy tablicy (czyli VARTYPE każdego elementu tablicy).

*dwElements*<br/>
Liczba elementów w tablicy. Można go zmienić po utworzeniu tablicy [ResizeOneDim](#resizeonedim).

*pvSrcData*<br/>
Wskaźnik do danych do skopiowania do tablicy.

*nLBound*<br/>
Dolna granica tablicy.

### <a name="remarks"></a>Uwagi

Funkcja przydziela i inicjuje dane dla tablicy, kopiując określone dane, jeśli wskaźnik *pvSrcData* nie ma wartości NULL.

W przypadku błędu, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

##  <a name="destroy"></a>  COleSafeArray::Destroy

Niszczy istniejących deskryptora tablicy i wszystkie dane w tablicy.

```
void Destroy();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekty są przechowywane w tablicy, każdy obiekt jest zwalniana. W przypadku błędu, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="destroydata"></a>  COleSafeArray::DestroyData

Niszczy wszystkich danych w bezpiecznej tablicy.

```
void DestroyData();
```

### <a name="remarks"></a>Uwagi

Jeśli obiekty są przechowywane w tablicy, każdy obiekt jest zwalniana. W przypadku błędu, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="destroydescriptor"></a>  COleSafeArray::DestroyDescriptor

Niszczy deskryptor bezpieczną tablicą.

```
void DestroyDescriptor();
```

### <a name="remarks"></a>Uwagi

W przypadku błędu, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="detach"></a>  COleSafeArray::Detach

Odłącza `VARIANT` dane z `COleSafeArray` obiektu.

```
VARIANT Detach();
```

### <a name="return-value"></a>Wartość zwracana

Podstawowe `VARIANT` wartość w `COleSafeArray` obiektu.

### <a name="remarks"></a>Uwagi

Funkcja odłącza danych w bezpiecznej tablicy, ustawiając VT_EMPTY VARTYPE obiektu. Odpowiada za wywołującego bezpłatne tablicy przez wywołanie funkcji Windows [VariantClear](/windows/desktop/api/oleauto/nf-oleauto-variantclear).

W przypadku błędu, funkcja zgłasza [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

  Zobacz przykład [COleSafeArray::PutElement](#putelement).

##  <a name="getbytearray"></a>  COleSafeArray::GetByteArray

Kopiuje zawartość do bezpiecznej tablicy do `CByteArray`.

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parametry

*Bajty*<br/>
Odwołanie do [CByteArray](../../mfc/reference/cbytearray-class.md) obiektu.

##  <a name="getdim"></a>  COleSafeArray::GetDim

Zwraca liczbę wymiarów `COleSafeArray` obiektu.

```
DWORD GetDim();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wymiarów w bezpiecznej tablicy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="getelement"></a>  COleSafeArray::GetElement

Pobiera pojedynczy element bezpieczną tablicą.

```
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parametry

*rgIndices*<br/>
Wskaźnik do tablicy indeksów dla każdego wymiaru tablicy.

*pvData*<br/>
Wskaźnik na położenie elementu tablicy.

### <a name="remarks"></a>Uwagi

Ta funkcja automatycznie wywołuje funkcje systemu windows `SafeArrayLock` i `SafeArrayUnlock` przed i po pobraniu elementu. Jeśli element danych jest ciąg, obiekt lub wariant, funkcja kopiuje element w prawidłowy sposób. Parametr *pvData* powinien wskazywać dużą wystarczająco dużego buforu zawiera element.

W przypadku błędu, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

##  <a name="getelemsize"></a>  COleSafeArray::GetElemSize

Pobiera rozmiar elementu w `COleSafeArray` obiektu.

```
DWORD GetElemSize();
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar w bajtach elementów bezpieczną tablicą.

##  <a name="getlbound"></a>  COleSafeArray::GetLBound

Zwraca dolną granicę dla żadnego wymiaru `COleSafeArray` obiektu.

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>Parametry

*dwDim*<br/>
Wymiar tablicy, dla którego należy pobrać dolną granicę.

*pLBound*<br/>
Wskaźnik do lokalizacji zwraca dolną granicę.

### <a name="remarks"></a>Uwagi

W przypadku błędu, funkcja zgłasza [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

##  <a name="getonedimsize"></a>  COleSafeArray::GetOneDimSize

Zwraca liczbę elementów w jednowymiarowy `COleSafeArray` obiektu.

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy jednowymiarowej bezpieczne.

### <a name="example"></a>Przykład

  Zobacz przykład [COleSafeArray::CreateOneDim](#createonedim).

##  <a name="getubound"></a>  COleSafeArray::GetUBound

Zwraca górną granicę dla każdego wymiaru tablicy bezpiecznej.

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>Parametry

*dwDim*<br/>
Wymiar tablicy, dla którego należy pobrać górną granicę.

*pUBound*<br/>
Wskaźnik do lokalizacji zwraca górną granicę.

### <a name="remarks"></a>Uwagi

W przypadku błędu, funkcja zgłasza [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

##  <a name="lock"></a>  COleSafeArray::Lock

Zwiększa liczbę blokad, tablicy i umieścić wskaźnik do tablicy danych deskryptora tablicy.

```
void Lock();
```

### <a name="remarks"></a>Uwagi

W przypadku błędu, wyniku weryfikacji zgłasza wyjątek [COleException](../../mfc/reference/coleexception-class.md).

Wskaźnik w deskryptorze tablicy jest prawidłowy do momentu `Unlock` jest wywoływana. Wywołania `Lock` mogą być zagnieżdżone; równą liczbę wywołań `Unlock` są wymagane.

Nie można usunąć tablicę, gdy jest on zablokowany.

##  <a name="operator_lpcvariant"></a>  COleSafeArray::operator LPCVARIANT

Wywołanie tego operatora rzutowania do dostępu do podstawowych `VARIANT` struktury, w tym `COleSafeArray` obiektu.

```
operator LPCVARIANT() const;
```

##  <a name="operator_lpvariant"></a>  COleSafeArray::operator LPVARIANT

Wywołanie tego operatora rzutowania do dostępu do podstawowych `VARIANT` struktury, w tym `COleSafeArray` obiektu.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Uwagi

Należy pamiętać, zmieniając wartość w `VARIANT` struktury używane przez wskaźnik zwracany przez tę funkcję zmieni wartość tego `COleSafeArray` obiektu.

##  <a name="operator_eq"></a>  COleSafeArray::operator =

Te operatory przeciążone przypisania skopiowany wartość źródłowa to `COleSafeArray` obiektu.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
  COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Uwagi

Krótki opis każdego operatora następująco:

- **Operator = (** *saSrc* **)** kopiuje istniejącą `COleSafeArray` obiektu do tego obiektu.

- **Operator = (** *varSrc* **)** kopiuje istniejącą `VARIANT` lub `COleVariant` tablicę do tego obiektu.

- **Operator = (** *pSrc* **)** kopie `VARIANT` obiektu array uzyskują *pSrc* do tego obiektu.

##  <a name="operator_eq_eq"></a>  COleSafeArray::operator ==

Ten operator porównuje dwie tablice (`SAFEARRAY`, `VARIANT`, `COleVariant`, lub `COleSafeArray` tablice) i zwraca wartość różną od zera, jeśli są równe; w przeciwnym razie 0.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Uwagi

Dwie tablice są równe, jeśli mają jednakową liczbę wymiarów, taki sam rozmiar każdego wymiaru i wartości równe elementów.

##  <a name="operator_lt_lt"></a>  COleSafeArray::operator &lt;&lt;

`COleSafeArray` Wstawiania (<<) — operator obsługuje diagnostycznych zrzucanie i przechowywania `COleSafeArray` obiektu do archiwum.

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

##  <a name="ptrofindex"></a>  COleSafeArray::PtrOfIndex

Zwraca wskaźnik do elementu określonego przez wartości indeksu.

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>Parametry

*rgIndices*<br/>
Tablica wartości indeksu, które identyfikują elementu tablicy. Należy określić wszystkie indeksy dla elementu.

*ppvData*<br/>
Powrót wskaźnika do elementu określonego przez wartości w *rgIndices*.

##  <a name="putelement"></a>  COleSafeArray::PutElement

Przypisuje jeden element w tablicy.

```
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parametry

*rgIndices*<br/>
Wskaźnik do tablicy indeksów dla każdego wymiaru tablicy.

*pvData*<br/>
Wskaźnik do danych, które można przypisać do tablicy. VT_DISPATCH VT_UNKNOWN i VT_BSTR typów variant wskaźników i nie wymagają innego poziomu pośredniego.

### <a name="remarks"></a>Uwagi

Ta funkcja automatycznie wywołuje funkcje Windows [SafeArrayLock](/windows/desktop/api/oleauto/nf-oleauto-safearraylock) i [SafeArrayUnlock](/windows/desktop/api/oleauto/nf-oleauto-safearrayunlock) przed i po przypisaniu elementu. Jeśli element danych jest ciąg, obiekt lub wariant, funkcja go został poprawnie skopiowany, a w przypadku ciąg, obiekt lub wariant istniejącego elementu jest poprawnie wyczyszczone.

Należy pamiętać, że masz kilka blokad w tablicy, dzięki czemu można umieścić elementy w tablicy, podczas gdy tablica jest zablokowany przez inne operacje.

W przypadku błędu, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

##  <a name="redim"></a>  COleSafeArray::Redim

Zmienia najmniej znaczący (po prawej stronie) granicę bezpiecznej tablicy.

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>Parametry

*psaboundNew*<br/>
Wskaźnik do nowej tablicy bezpieczne powiązany struktury zawierającej nowej granicy tablicy. Tylko najmniej znaczącego wymiaru tablicy mogą ulec zmianie.

### <a name="remarks"></a>Uwagi

W przypadku błędu, funkcja zgłasza [COleException](../../mfc/reference/coleexception-class.md).

##  <a name="resizeonedim"></a>  COleSafeArray::ResizeOneDim

Zmienia liczbę elementów w jednowymiarowym `COleSafeArray` obiektu.

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>Parametry

*dwElements*<br/>
Liczba elementów w tablicy jednowymiarowej bezpieczne.

### <a name="remarks"></a>Uwagi

W przypadku błędu, funkcja zgłasza [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

  Zobacz przykład [COleSafeArray::CreateOneDim](#createonedim).

##  <a name="unaccessdata"></a>  COleSafeArray::UnaccessData

Dekrementuje blokada count tablicę i unieważnia wskaźnika pobierane przez `AccessData`.

```
void UnaccessData();
```

### <a name="remarks"></a>Uwagi

W przypadku błędu, funkcja zgłasza [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Przykład

  Zobacz przykład [COleSafeArray::AccessData](#accessdata).

##  <a name="unlock"></a>  COleSafeArray::Unlock

Zmniejsza liczbę blokad tablicy, może być zwolniona lub zmiany rozmiaru.

```
void Unlock();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana po zakończeniu dostępu do danych w tablicy. W przypadku błędu, wyniku weryfikacji zgłasza wyjątek [COleException](../../mfc/reference/coleexception-class.md).

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleVariant](../../mfc/reference/colevariant-class.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
