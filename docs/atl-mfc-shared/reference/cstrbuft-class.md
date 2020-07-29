---
title: Klasa CStrBufT
ms.date: 10/18/2018
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
ms.openlocfilehash: 4d9d0b403e572d6fdea65355702467c89587cc3a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219082"
---
# <a name="cstrbuft-class"></a>Klasa CStrBufT

Ta klasa umożliwia automatyczne czyszczenie zasobów `GetBuffer` i `ReleaseBuffer` wywoływanie na istniejącym `CStringT` obiekcie.

## <a name="syntax"></a>Składnia

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>Parametry

*TCharType*<br/>
Typ znaku `CStrBufT` klasy. Może być jedną z następujących czynności:

- **`char`**(dla ciągów znaków ANSI)

- **`wchar_t`**(dla ciągów znaków Unicode)

- Używanie TCHAR (dla ciągów znaków ANSI i Unicode)

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|PCXSTR|Wskaźnik do stałego ciągu.|
|PXSTR|Wskaźnik do ciągu.|
|`StringType`|Typ ciągu, którego bufor ma być manipulowany przez specjalizacje tego szablonu klasy.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|Konstruktor dla obiektu buforu ciągu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStrBufT:: SetLength](#setlength)|Ustawia długość buforu znaków skojarzonego obiektu ciągu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStrBufT:: operator PCXSTR](#operator_pcxstr)|Pobiera **`const`** wskaźnik do buforu znaków skojarzonego obiektu ciągu.|
|[CStrBufT:: operator PXSTR](#operator_pxstr)|Pobiera wskaźnik do buforu znaków skojarzonego obiektu ciągu.|

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStrBufT:: AUTO_LENGTH](#auto_length)|Automatycznie Ustal nową długość ciągu w wersji.|
|[CStrBufT:: SET_LENGTH](#set_length)|Ustaw długość obiektu String w czasie GetBuffer|

## <a name="remarks"></a>Uwagi

Ta klasa jest używana jako Klasa otoki do zamiany wywołań do [GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) i [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer), lub [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) i `ReleaseBuffer` .

Głównie zaprojektowana jako Klasa pomocnika `CStrBufT` zapewnia wygodną metodę pracy dewelopera z buforem znaków obiektu String bez obaw o sposób lub czas wywoływania `ReleaseBuffer` . Jest to możliwe, ponieważ obiekt otoki wykracza poza zakres naturalnie w przypadku wyjątku lub wielu wyjść ze ścieżki kodu; powoduje, że destruktor zwolni zasób ciągu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr. h

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a>CStrBufT:: AUTO_LENGTH

Automatycznie Ustal nową długość ciągu w wersji.

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>Uwagi

Automatycznie Ustal nową długość ciągu w wersji. Ciąg musi być zakończony znakiem null.

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a>CStrBufT::CStrBufT

Konstruuje obiekt buforu.

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Obiekt ciągu skojarzony z buforem. Zazwyczaj deweloper będzie używać wstępnie zdefiniowanych elementów typedef of `CStrBuf` (używanie TCHAR Variant), `CStrBufA` ( **`char`** Variant) i `CStrBufW` ( **`wchar_t`** Variant).

*nMinLength*<br/>
Minimalna długość buforu znaków.

*flagiDW*<br/>
Określa, czy długość ciągu jest określana automatycznie. Może być jedną z następujących czynności:

- AUTO_LENGTH długość ciągu jest określana automatycznie, gdy jest wywoływana [CSimpleStringT:: Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) . Ciąg musi być zakończony znakiem null. Wartość domyślna.

- SET_LENGTH długość ciągu jest ustawiana, gdy wywoływana jest [CSimpleStringT:: GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) .

### <a name="remarks"></a>Uwagi

Tworzy bufor ciągu dla skojarzonego obiektu ciągu. Podczas konstruowania jest wywoływana [CSimpleStringT:: GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) lub [CSimpleStringT:: GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) .

Należy pamiętać, że Konstruktor kopiujący jest **`private`** .

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a>CStrBufT:: operator PCXSTR

Bezpośrednio uzyskuje dostęp do znaków przechowywanych w skojarzonym obiekcie ciągu jako ciąg w stylu języka C.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik znaku do danych ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zwrócić wskaźnik do buforu znaków obiektu ciągu. Zawartości obiektu String nie można zmienić za pomocą tego wskaźnika.

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a>CStrBufT:: operator PXSTR

Bezpośrednio uzyskuje dostęp do znaków przechowywanych w skojarzonym obiekcie ciągu jako ciąg w stylu języka C.

```
operator PXSTR() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik znaku do danych ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zwrócić wskaźnik do buforu znaków obiektu ciągu. Deweloper może zmienić zawartość obiektu ciągu z tym wskaźnikiem.

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a>CStrBufT::P CXSTR

Wskaźnik do stałego ciągu.

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a>CStrBufT::P XSTR

Wskaźnik do ciągu.

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a>CStrBufT:: SET_LENGTH

Ustaw długość obiektu String w `GetBuffer` czasie.

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>Uwagi

Ustaw długość obiektu String w czasie GetBuffer.

Określa, czy [CSimpleStringT:: GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) i [CSimpleStringT:: GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) są wywoływane podczas konstruowania obiektu buforu ciągu.

## <a name="cstrbuftsetlength"></a><a name="setlength"></a>CStrBufT:: SetLength

Ustawia długość buforu znaków.

```cpp
void SetLength(int nLength);
```

### <a name="parameters"></a>Parametry

*nLength*<br/>
Nowa długość buforu znaków w obiekcie String.

> [!NOTE]
> Wartość musi być mniejsza lub równa minimalnej długości buforu określonej w konstruktorze `CStrBufT` .

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby ustawić długość ciągu reprezentowanego przez obiekt buforu.

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a>CStrBufT:: StringType

Typ ciągu, którego bufor ma być manipulowany przez specjalizacje tego szablonu klasy.

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>Uwagi

`TCharType`to typ znaku służący do specjalizacji szablonu klasy.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
