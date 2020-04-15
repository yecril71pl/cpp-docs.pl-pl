---
title: CStrBufT, klasa
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
ms.openlocfilehash: 84c67aa8ea819f420368a72a2374f800f3d89055
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317646"
---
# <a name="cstrbuft-class"></a>CStrBufT, klasa

Ta klasa zapewnia automatyczne `GetBuffer` oczyszczanie zasobów `ReleaseBuffer` `CStringT` i wywołuje istniejący obiekt.

## <a name="syntax"></a>Składnia

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>Parametry

*Typ TChar*<br/>
Typ znaku `CStrBufT` klasy. Może być jedną z następujących czynności:

- **char** (dla ciągów znaków ANSI)

- **wchar_t** (dla ciągów znaków Unicode)

- TCHAR (zarówno dla ciągów znaków ANSI, jak i Unicode)

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|SZTXSTR|Wskaźnik do stałego ciągu.|
|PXSTR ( PXSTR )|Wskaźnik do ciągu.|
|`StringType`|Typ ciągu, którego bufor ma być manipulowany przez specjalizacje tego szablonu klasy.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|Konstruktor dla obiektu buforu ciągu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStrBufT::SetLength](#setlength)|Ustawia długość buforu znaków skojarzonego obiektu ciągu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStrBufT::operator PCXSTR](#operator_pcxstr)|Pobiera wskaźnik **const** do buforu znaków skojarzonego obiektu ciągu.|
|[CStrBufT::operator PXSTR](#operator_pxstr)|Pobiera wskaźnik do buforu znaków skojarzonego obiektu ciągu.|

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStrBufT::AUTO_LENGTH](#auto_length)|Automatycznie określ nową długość ciągu w wydaniu.|
|[CStrBufT::SET_LENGTH](#set_length)|Ustawianie długości obiektu ciągu w czasie GetBuffer|

## <a name="remarks"></a>Uwagi

Ta klasa jest używana jako klasa otoki do zastępowania wywołań [GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) i [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)lub [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) i `ReleaseBuffer`.

Zaprojektowany przede wszystkim jako klasa `CStrBufT` pomocnicza, zapewnia wygodny sposób dla dewelopera do pracy z buforem `ReleaseBuffer`znaków obiektu ciągu bez martwienia się o to, jak i kiedy wywołać . Jest to możliwe, ponieważ obiekt otoki wykracza poza zakres naturalnie w przypadku wyjątku lub wielu ścieżek kodu zamykania; powodując jego destruktora, aby zwolnić zasób ciągu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr.h

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a>CStrBufT::AUTO_LENGTH

Automatycznie określ nową długość ciągu w wydaniu.

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>Uwagi

Automatycznie określ nową długość ciągu w wydaniu. Ciąg musi być zakończony zerem.

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a>CStrBufT::CStrBufT

Konstruuje obiekt buforu.

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Obiekt ciągu skojarzony z buforem. Zazwyczaj `CStrBuf` deweloper użyje wstępnie zdefiniowanych typedefs (wariant TCHAR), `CStrBufA` ( wariant**char)** i `CStrBufW` **(wchar_t** wariant).

*nMinLength (Niem.*<br/>
Minimalna długość buforu znaków.

*Dwflags*<br/>
Określa, czy długość ciągu jest określana automatycznie. Może być jedną z następujących czynności:

- AUTO_LENGTH długość ciągu jest automatycznie określana, gdy [CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) jest wywoływana. Ciąg musi być zakończony zerem. Wartość domyślna.

- SET_LENGTH długość ciągu jest ustawiana, gdy wywoływana jest [nazwa CSimpleStringT::GetBuffer.](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)

### <a name="remarks"></a>Uwagi

Tworzy bufor ciągów dla skojarzonego obiektu ciągu. Podczas budowy [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) lub [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) jest wywoływana.

Należy zauważyć, że konstruktor kopii jest **prywatny**.

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a>CStrBufT::operator PCXSTR

Bezpośredni dostęp do znaków przechowywanych w skojarzonym obiekcie ciągu jako ciąg w stylu C.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik znaku do danych ciągu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zwrócić wskaźnik do buforu znaków obiektu ciągu. Zawartość obiektu ciągu nie można zmienić za pomocą tego wskaźnika.

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a>CStrBufT::operator PXSTR

Bezpośredni dostęp do znaków przechowywanych w skojarzonym obiekcie ciągu jako ciąg w stylu C.

```
operator PXSTR() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik znaku do danych ciągu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby zwrócić wskaźnik do buforu znaków obiektu ciągu. Deweloper może zmienić zawartość obiektu ciągu za pomocą tego wskaźnika.

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a>CStrBufT::PCXSTR

Wskaźnik do stałego ciągu.

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a>CStrBufT::PXSTR

Wskaźnik do ciągu.

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a>CStrBufT::SET_LENGTH

Ustaw długość obiektu ciągu `GetBuffer` w czasie.

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>Uwagi

Ustaw długość obiektu ciągu w czasie GetBuffer.

Określa, czy [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) i [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) są wywoływane, gdy obiekt buforu ciągu jest skonstruowany.

## <a name="cstrbuftsetlength"></a><a name="setlength"></a>CStrBufT::SetLength

Ustawia długość buforu znaków.

```
void SetLength(int nLength);
```

### <a name="parameters"></a>Parametry

*nLength (nLength)*<br/>
Nowa długość buforu znaków obiektu ciągu.

> [!NOTE]
> Musi być mniejsza lub równa minimalnej długości buforu `CStrBufT`określonej w konstruktorze .

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby ustawić długość ciągu reprezentowanego przez obiekt buforu.

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a>CStrBufT::Rodzaj ciągu

Typ ciągu, którego bufor ma być manipulowany przez specjalizacje tego szablonu klasy.

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>Uwagi

`TCharType`jest typem znaku używanym do specjalizacji szablonu klasy.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
