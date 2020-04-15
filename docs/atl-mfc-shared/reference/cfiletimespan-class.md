---
title: CFileTimeSpan, klasa
description: Klasa Active Template Library (ATL) i Microsoft Foundation Classes (MFC) CFileTimeSpan zarządza interwałami czasowymi w jednostkach FILETIME.
ms.date: 01/10/2020
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
ms.openlocfilehash: 87737ea1c778660a68510b484bcdfa3a4670e8ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317854"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan, klasa

Ta klasa zawiera metody zarządzania względnymi wartościami daty i godziny skojarzonymi z plikiem.

## <a name="syntax"></a>Składnia

```cpp
class CFileTimeSpan
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktorzy publiczni

|Nazwa|Opis|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Wywołanie tej metody, aby pobrać `CFileTimeSpan` przedział czasu z obiektu.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Wywołanie tej metody, aby `CFileTimeSpan` ustawić przedział czasu obiektu.|

### <a name="public-operators"></a>Operatorzy publiczni

|Nazwa|Opis|
|----------|-----------------|
|[CFileTimeSpan::operator -](#operator_-)|Wykonuje odejmowanie `CFileTimeSpan` obiektu.|
|[CFileTimeSpan::operator !=](#operator_neq)|Porównuje dwa `CFileTimeSpan` obiekty dla nierówności.|
|[CFileTimeSpan::operator +](#operator_add)|Wykonuje dodawanie na `CFileTimeSpan` obiekcie.|
|[CFileTimeSpan::operator +=](#operator_add_eq)|Wykonuje dodawanie obiektu `CFileTimeSpan` i przypisuje wynik do bieżącego obiektu.|
|[CFileTimeSpan::operator&lt;](#operator_lt)|Porównuje dwa `CFileTimeSpan` obiekty, aby określić mniejsze.|
|[CFileTimeSpan::operator&lt;=](#operator_lt_eq)|Porównuje dwa `CFileTimeSpan` obiekty, aby określić równość lub mniejsze.|
|[CFileTimeSpan::operator =](#operator_eq)|Operator przypisania.|
|[CFileTimeSpan::operator -=](#operator_-_eq)|Wykonuje odejmowanie `CFileTimeSpan` obiektu i przypisuje wynik do bieżącego obiektu.|
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Porównuje dwa `CFileTimeSpan` obiekty dla równości.|
|[CFileTimeSpan::operator&gt;](#operator_gt)|Porównuje dwa `CFileTimeSpan` obiekty, aby określić większy.|
|[CFileTimeSpan::operator&gt;=](#operator_gt_eq)|Porównuje dwa `CFileTimeSpan` obiekty, aby określić równość lub większe.|

## <a name="remarks"></a>Uwagi

Klasa `CFileTimeSpan` zawiera metody do obsługi względnych okresów czasu w jednostkach używanych przez system plików. Jednostki te są często używane w operacjach na temat plików, na przykład podczas tworzenia pliku, ostatnio dostępnego lub ostatnio modyfikowanego. Metody tej klasy są często używane w połączeniu z [CFileTime obiektów klasy.](../../atl-mfc-shared/reference/cfiletime-class.md)

## <a name="example"></a>Przykład

Zobacz przykład [CFileTime::Milisekunda](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltime.h

## <a name="cfiletimespancfiletimespan"></a><a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

Konstruktor.

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Istniejący `CFileTimeSpan` obiekt.

*nSpan (własna)*\
Okres czasu w jednostkach FILETIME.

### <a name="remarks"></a>Uwagi

Obiekt `CFileTimeSpan` można utworzyć przy `CFileTimeSpan` użyciu istniejącego obiektu lub wyrazić jako wartość 64-bitową w jednostkach 100-nanosekundy FILETIME. Aby uzyskać więcej informacji, zobacz [CFileTime](cfiletime-class.md). Domyślny konstruktor ustawia przedział czasu na 0.

## <a name="cfiletimespangettimespan"></a><a name="gettimespan"></a>CFileTimeSpan::GetTimeSpan

Wywołanie tej metody, aby pobrać `CFileTimeSpan` przedział czasu z obiektu.

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca przedział czasu w jednostkach 100 nanosekundy FILETIME. Aby uzyskać więcej informacji, zobacz [CFileTime](cfiletime-class.md).

## <a name="cfiletimespanoperator--"></a><a name="operator_-"></a>CFileTimeSpan::operator -

Wykonuje odejmowanie `CFileTimeSpan` obiektu.

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Obiekt `CFileTimeSpan`.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CFileTimeSpan` obiekt reprezentujący wynik różnicy między dwoma przedziałami czasu.

## <a name="cfiletimespanoperator-"></a><a name="operator_neq"></a>CFileTimeSpan::operator !=

Porównuje dwa `CFileTimeSpan` obiekty dla nierówności.

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Obiekt `CFileTimeSpan` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany element `CFileTimeSpan` nie jest równy obiektowi; w przeciwnym razie FALSE.

## <a name="cfiletimespanoperator-"></a><a name="operator_add"></a>CFileTimeSpan::operator +

Wykonuje dodawanie na `CFileTimeSpan` obiekcie.

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Obiekt `CFileTimeSpan`.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CFileTimeSpan` obiekt zawierający sumę dwóch przedziałów czasowych.

## <a name="cfiletimespanoperator-"></a><a name="operator_add_eq"></a>CFileTimeSpan::operator +=

Wykonuje dodawanie obiektu `CFileTimeSpan` i przypisuje wynik do bieżącego obiektu.

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Obiekt `CFileTimeSpan`.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTimeSpan` obiekt zawierający sumę dwóch przedziałów czasowych.

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt"></a>CFileTimeSpan::operator&lt;

Porównuje dwa `CFileTimeSpan` obiekty, aby określić mniejsze.

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Obiekt `CFileTimeSpan` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest mniejszy (czyli reprezentuje krótszy okres czasu) niż drugi, w przeciwnym razie FALSE.

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt_eq"></a>CFileTimeSpan::operator&lt;=

Porównuje dwa `CFileTimeSpan` obiekty, aby określić równość lub mniejsze.

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Obiekt `CFileTimeSpan` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest mniejszy niż (czyli reprezentuje krótszy okres czasu) lub równy drugiemu, w przeciwnym razie FALSE.

## <a name="cfiletimespanoperator-"></a><a name="operator_eq"></a>CFileTimeSpan::operator =

Operator przypisania.

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Obiekt `CFileTimeSpan`.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTimeSpan` obiekt.

## <a name="cfiletimespanoperator--"></a><a name="operator_-_eq"></a>CFileTimeSpan::operator -=

Wykonuje odejmowanie `CFileTimeSpan` obiektu i przypisuje wynik do bieżącego obiektu.

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Obiekt `CFileTimeSpan`.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTimeSpan` obiekt.

## <a name="cfiletimespanoperator-"></a><a name="operator_eq_eq"></a>CFileTimeSpan::operator ==

Porównuje dwa `CFileTimeSpan` obiekty dla równości.

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Obiekt `CFileTimeSpan` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obiekty są równe, w przeciwnym razie FALSE.

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt"></a>CFileTimeSpan::operator&gt;

Porównuje dwa `CFileTimeSpan` obiekty, aby określić większy.

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Obiekt `CFileTimeSpan` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest większy niż (oznacza to, że reprezentuje dłuższy okres czasu) niż drugi, w przeciwnym razie FALSE.

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt_eq"></a>CFileTimeSpan::operator&gt;=

Porównuje dwa `CFileTimeSpan` obiekty, aby określić równość lub większe.

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*\
Obiekt `CFileTimeSpan` do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest większy niż (oznacza to, że reprezentuje dłuższy okres czasu) lub równy drugiemu, w przeciwnym razie FALSE.

## <a name="cfiletimespansettimespan"></a><a name="settimespan"></a>CFileTimeSpan::SetTimeSpan

Wywołanie tej metody, aby `CFileTimeSpan` ustawić przedział czasu obiektu.

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*nSpan (własna)*\
Nowa wartość dla przedziału czasu w jednostkach FILETIME 100 nanosekund. Aby uzyskać więcej informacji, zobacz [CFileTime](cfiletime-class.md).

## <a name="see-also"></a>Zobacz też

[Filetime](/windows/win32/api/minwinbase/ns-minwinbase-filetime)\
[CFileTime, klasa](cfiletime-class.md)\
[Wykres hierarchii](../../mfc/hierarchy-chart.md)\
[Zajęcia udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
