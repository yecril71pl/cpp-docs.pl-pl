---
title: CStrBufT Class
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
ms.openlocfilehash: 81c3b429089eab3ba95c178e3fc7cf2bf55783a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223496"
---
# <a name="cstrbuft-class"></a>CStrBufT Class

Ta klasa udostępnia Oczyszczanie zasobów automatyczne dla `GetBuffer` i `ReleaseBuffer` wywołuje na istniejącym `CStringT` obiektu.

## <a name="syntax"></a>Składnia

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>Parametry

*TCharType*<br/>
Typ znaku `CStrBufT` klasy. Może to być jeden z następujących elementów:

- **CHAR** (na ciągi znaków ANSI)

- **wchar_t** (na ciągi znaków Unicode)

- TCHAR (na ciągi znaków ANSI i Unicode)

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|PCXSTR|Wskaźnik ze stałym ciągiem.|
|PXSTR|Wskaźnik do ciągu.|
|`StringType`|Typu ciąg, którego bufor ma być manipulowane przez specjalizacje szablonu klasy.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|Konstruktor obiektu buforu ciągu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStrBufT::SetLength](#setlength)|Ustawia długość buforu znaku ciągu skojarzonego obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStrBufT::operator PCXSTR](#operator_pcxstr)|Pobiera **const** wskaźnik do buforu znaków ciągu skojarzonego obiektu.|
|[CStrBufT::operator PXSTR](#operator_pxstr)|Pobiera wskaźnik do buforu znaków ciągu skojarzonego obiektu.|

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[CStrBufT::AUTO_LENGTH](#auto_length)|Automatycznie określić nową długość ciągu w wersji.|
|[CStrBufT::SET_LENGTH](#set_length)|Ustawianie długości z obiektem ciągu w czasie getbuffer —|

## <a name="remarks"></a>Uwagi

Ta klasa jest używana jako klasa otoki do zastępowania wywołań do [getbuffer —](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) i [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer), lub [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) i `ReleaseBuffer`.

Przeznaczony głównie jako klasę Pomocnika `CStrBufT` zapewnia wygodny sposób projektanta do pracy z buforu znaków obiektu ciągu, nie martwiąc się o tym, jak i kiedy wywołać metodę `ReleaseBuffer`. Jest to możliwe, ponieważ obiekt otoki wykracza poza zakres, naturalny sposób w przypadku wyjątku lub wielu istniejącej ścieżki kodu. powoduje jego destruktor zwolnić zasobu ciągu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr.h

##  <a name="auto_length"></a>  CStrBufT::AUTO_LENGTH

Automatycznie określić nową długość ciągu w wersji.

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>Uwagi

Automatycznie określić nową długość ciągu w wersji. Ciąg musi być zakończony znakiem null.

##  <a name="cstrbuft"></a>  CStrBufT::CStrBufT

Tworzy obiekt buforu.

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Obiekt ciągu skojarzonego z buforu. Zwykle, deweloper będzie używać wstępnie zdefiniowanych definicje typów `CStrBuf` (TCHAR), wariant `CStrBufA` (**char** wariant) i `CStrBufW` (**wchar_t** wariant).

*nMinLength*<br/>
Minimalna długość buforu znaków.

*dwFlags*<br/>
Określa, jeśli długość ciągu jest ustalany automatycznie. Może to być jeden z następujących elementów:

- Długość ciągu AUTO_LENGTH są automatycznie określane podczas [CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) jest wywoływana. Ciąg musi być zakończony znakiem null. Wartość domyślna.

- Długość ciągu SET_LENGTH jest ustawiona, gdy [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) jest wywoływana.

### <a name="remarks"></a>Uwagi

Powoduje utworzenie buforu ciągu dla obiektu skojarzonego ciągu. Podczas konstruowania [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) lub [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) jest wywoływana.

Należy zauważyć, że Konstruktor kopiujący **prywatnej**.

##  <a name="operator_pcxstr"></a>  CStrBufT::operator PCXSTR

Bezpośrednio uzyskuje dostęp do znaków przechowywanych w obiekcie skojarzone ciągu jako ciąg stylu C.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik znaku do danych ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zwrócić wskaźnik do buforu znaku obiektu ciągu. Zawartość z obiektem ciągu nie można zmienić za pomocą tego wskaźnika.

##  <a name="operator_pxstr"></a>  CStrBufT::operator PXSTR

Bezpośrednio uzyskuje dostęp do znaków przechowywanych w obiekcie skojarzone ciągu jako ciąg stylu C.

```
operator PXSTR() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik znaku do danych ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby zwrócić wskaźnik do buforu znaku obiektu ciągu. Deweloper może zmienić zawartość z obiektem ciągu za pomocą tego wskaźnika.

##  <a name="pcxstr"></a>  CStrBufT::PCXSTR

Wskaźnik ze stałym ciągiem.

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

##  <a name="pxstr"></a>  CStrBufT::PXSTR

Wskaźnik do ciągu.

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

##  <a name="set_length"></a>  CStrBufT::SET_LENGTH

Ustawianie długości z obiektem ciągu w `GetBuffer` czasu.

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>Uwagi

Ustawianie długości z obiektem ciągu w czasie getbuffer —.

Określa, czy [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) i [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) są wywoływane, gdy obiekt buforu ciągu jest konstruowany.

##  <a name="setlength"></a>  CStrBufT::SetLength

Ustawia długość buforu znaków.

```
void SetLength(int nLength);
```

### <a name="parameters"></a>Parametry

*nLength*<br/>
Nową długość buforu znaków ciągu obiektu.

> [!NOTE]
>  Musi być mniejsza niż długość minimalna buforu określony w Konstruktorze typu `CStrBufT`.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby ustawić długość ciągu, reprezentowane przez obiekt buforu.

##  <a name="stringtype"></a>  CStrBufT::StringType

Typu ciąg, którego bufor ma być manipulowane przez specjalizacje szablonu klasy.

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>Uwagi

`TCharType` jest to typ znaku używany specjalizacja szablonu klasy.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
