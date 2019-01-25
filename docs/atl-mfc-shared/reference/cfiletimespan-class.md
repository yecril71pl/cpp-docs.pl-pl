---
title: CFileTimeSpan Class
ms.date: 10/18/2018
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
ms.openlocfilehash: 8d384ced5de588a348eb72b9852697694b370ee4
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894162"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan Class

Ta klasa dostarcza metody do zarządzania względne wartości daty i godziny skojarzonych z plikiem.

## <a name="syntax"></a>Składnia

```
class CFileTimeSpan
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Wywołaj tę metodę, aby pobrać przedział czasu od `CFileTimeSpan` obiektu.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Wywołaj tę metodę, aby ustawić zakres czasu `CFileTimeSpan` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileTimeSpan::operator -](#operator_-)|Wykonuje odejmowanie `CFileTimeSpan` obiektu.|
|[CFileTimeSpan::operator! =](#operator_neq)|Porównuje dwa `CFileTimeSpan` obiekty pod kątem nierówności.|
|[CFileTimeSpan::operator +](#operator_add)|Wykonuje dodawanie na `CFileTimeSpan` obiektu.|
|[CFileTimeSpan::operator +=](#operator_add_eq)|Wykonuje dodawanie na `CFileTimeSpan` obiektu i przypisz wynik do bieżącego obiektu.|
|[CFileTimeSpan::operator &lt;](#operator_lt)|Porównuje dwa `CFileTimeSpan` obiektów, aby określić mniejszy.|
|[CFileTimeSpan::operator &lt;=](#operator_lt_eq)|Porównuje dwa `CFileTimeSpan` obiektów, aby określić równości lub mniejszy.|
|[CFileTimeSpan::operator =](#operator_eq)|Operator przypisania.|
|[CFileTimeSpan::operator-=](#operator_-_eq)|Wykonuje odejmowanie `CFileTimeSpan` obiektu i przypisz wynik do bieżącego obiektu.|
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Porównuje dwa `CFileTimeSpan` obiekty pod kątem równości.|
|[CFileTimeSpan::operator &gt;](#operator_gt)|Porównuje dwa `CFileTimeSpan` obiektów, aby określić wyższy.|
|[CFileTimeSpan::operator &gt;=](#operator_gt_eq)|Porównuje dwa `CFileTimeSpan` obiektów, aby określić równości lub większy.|

## <a name="remarks"></a>Uwagi

Ta klasa dostarcza metody zarządzania względne okresy czasu, często napotkano podczas wykonywania operacji dotyczących, kiedy plik został utworzony, ostatnim uzyskaniu dostępu do lub Data ostatniej modyfikacji. Metody tej klasy są często używane w połączeniu z [CFileTime, klasa](../../atl-mfc-shared/reference/cfiletime-class.md) obiektów.

## <a name="example"></a>Przykład

Zobacz przykład [CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltime.h

##  <a name="cfiletimespan"></a>  CFileTimeSpan::CFileTimeSpan

Konstruktor.

```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
Istniejące `CFileTimeSpan` obiektu.

*nSpan*<br/>
Okres czasu w milisekundach.

### <a name="remarks"></a>Uwagi

`CFileTimeSpan` Obiektu można utworzyć przy użyciu istniejącego `CFileTimeSpan` obiektu lub wyrażonej w postaci wartości 64-bitowych. Domyślny konstruktor ustawia przedział czasu na 0.

##  <a name="gettimespan"></a>  CFileTimeSpan::GetTimeSpan

Wywołaj tę metodę, aby pobrać przedział czasu od `CFileTimeSpan` obiektu.

```
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca przedział czasu w milisekundach.

##  <a name="operator_-"></a>  CFileTimeSpan::operator-

Wykonuje odejmowanie `CFileTimeSpan` obiektu.

```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CFileTimeSpan` obiekt reprezentujący wynik różnicę między dwoma okresów.

##  <a name="operator_neq"></a>  CFileTimeSpan::operator! =

Porównuje dwa `CFileTimeSpan` obiekty pod kątem nierówności.

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
`CFileTimeSpan` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli element, którą jest porównywany nie jest równa `CFileTimeSpan` obiektu; w przeciwnym razie wartość FALSE.

##  <a name="operator_add"></a>  CFileTimeSpan::operator +

Wykonuje dodawanie na `CFileTimeSpan` obiektu.

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CFileTimeSpan` obiektu zawierającą sumę dwóch czasu obejmuje.

##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator +=

Wykonuje dodawanie na `CFileTimeSpan` obiektu, a następnie przypisuje wynik, jak bieżący obiekt.

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTimeSpan` obiektu zawierającą sumę dwóch czasu obejmuje.

##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;

Porównuje dwa `CFileTimeSpan` obiektów, aby określić mniejszy.

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
`CFileTimeSpan` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest mniejszy (czyli reprezentuje krótszy okres) od drugiej, w przeciwnym razie wartość FALSE.

##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=

Porównuje dwa `CFileTimeSpan` obiektów, aby określić równości lub mniejszy.

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
`CFileTimeSpan` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest mniejszy od (czyli reprezentuje krótszy okres) lub równe drugiemu, w przeciwnym razie wartość FALSE.

##  <a name="operator_eq"></a>  CFileTimeSpan::operator =

Operator przypisania.

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTimeSpan` obiektu.

##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator-=

Wykonuje odejmowanie `CFileTimeSpan` obiektu, a następnie przypisuje wynik, jak bieżący obiekt.

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
Element `CFileTimeSpan` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowany `CFileTimeSpan` obiektu.

##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==

Porównuje dwa `CFileTimeSpan` obiekty pod kątem równości.

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
`CFileTimeSpan` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obiekty są równe, w przeciwnym razie wartość FALSE.

##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;

Porównuje dwa `CFileTimeSpan` obiektów, aby określić wyższy.

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
`CFileTimeSpan` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest większy niż (czyli reprezentuje dłuższy okres czasu) od drugiej, w przeciwnym razie wartość FALSE.

##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=

Porównuje dwa `CFileTimeSpan` obiektów, aby określić równości lub większy.

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*zakres*<br/>
`CFileTimeSpan` Obiekt do porównania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli pierwszy obiekt jest większy niż (czyli reprezentuje dłuższy okres czasu) lub równe drugiemu, w przeciwnym razie wartość FALSE.

##  <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan

Wywołaj tę metodę, aby ustawić zakres czasu `CFileTimeSpan` obiektu.

```
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*nSpan*<br/>
Nowa wartość dla zakresu czasu w milisekundach.

## <a name="see-also"></a>Zobacz też

[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTime, klasa](../../atl-mfc-shared/reference/cfiletime-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
