---
title: Klasa CDumpContext
ms.date: 11/04/2016
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
ms.openlocfilehash: a5b53ced4e20c920aab8e7ebcda3e3f6f8798ba5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164101"
---
# <a name="cdumpcontext-class"></a>Klasa CDumpContext

Obsługuje zorientowane na strumień diagnostyczne dane wyjściowe w postaci tekstu czytelny dla człowieka.

## <a name="syntax"></a>Składnia

```
class CDumpContext
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDumpContext::CDumpContext](#cdumpcontext)|Konstruuje `CDumpContext` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDumpContext::DumpAsHex](#dumpashex)|Zrzuca element wskazane w formacie szesnastkowym.|
|[CDumpContext::Flush](#flush)|Czyści wszystkie dane w buforze kontekstu zrzutu.|
|[CDumpContext::GetDepth](#getdepth)|Pobiera całkowitą głębokość zrzutu.|
|[CDumpContext::HexDump](#hexdump)|Zrzuca bajtów zawartych w tablicy w formacie szesnastkowym.|
|[CDumpContext::SetDepth](#setdepth)|Ustawia głębię zrzutu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDumpContext::operator &lt;&lt;](#operator_lt_lt)|Wstawia zmienne i obiekty w kontekście zrzutu.|

## <a name="remarks"></a>Uwagi

`CDumpContext` nie ma klasy bazowej.

Możesz użyć [afxDump](diagnostic-services.md#afxdump), zadeklarowane wstępnie `CDumpContext` obiektu większość swojej zrzucania. `afxDump` Obiekt jest dostępny tylko w wersji debugowania biblioteki klas Microsoft Foundation.

Kilka pamięci [usługi diagnostyczne](../../mfc/reference/diagnostic-services.md) użyj `afxDump` dla swoich danych wyjściowych.

W obszarze środowiska Windows, dane wyjściowe z predefiniowanych `afxDump` obiektu zachowuje się podobnie jak `cerr` strumienia, jest kierowany do debugera za pomocą funkcji Windows `OutputDebugString`.

`CDumpContext` Klasa ma przeciążonej wstawiania ( **<<**) operator `CObject` wskaźników, które zrzuty danych obiektu. Jeśli potrzebujesz format niestandardowy zrzutu dla obiektu pochodnych zastępują [CObject::Dump](../../mfc/reference/cobject-class.md#dump). Większość klas Microsoft Foundation zaimplementować zastąpione `Dump` funkcja elementu członkowskiego.

Klasy, które nie pochodzą z `CObject`, takich jak `CString`, `CTime`, i `CTimeSpan`, ma swoje własne przeciążona `CDumpContext` operatorów wstawiania, jako struktury są często używane, takich jak `CFileStatus`, `CPoint`, i `CRect`.

Jeśli używasz [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) lub [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) makra w implementacji klasy, a następnie `CObject::Dump` zostanie wydrukowany nazwę Twojego `CObject`-klasy pochodnej. W przeciwnym razie zostanie wydrukowany `CObject`.

`CDumpContext` Klasy jest dostępna zarówno debugowania, jak i wydania wersji biblioteki, ale `Dump` funkcja członkowska jest zdefiniowane tylko w wersji do debugowania. Użyj **#ifdef _DEBUG**  /  `#endif` instrukcje dopasowywanie diagnostyki kodu, w tym niestandardowych `Dump` funkcji elementów członkowskich.

Przed przystąpieniem do tworzenia własnych `CDumpContext` obiektu, należy utworzyć `CFile` obiekt, który służy jako miejsce docelowe zrzutu.

Aby uzyskać więcej informacji na temat `CDumpContext`, zobacz [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CDumpContext`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="cdumpcontext"></a>  CDumpContext::CDumpContext

Tworzy obiekt klasy `CDumpContext`.

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Wskaźnik do `CFile` obiekt, który jest miejscem docelowym zrzutu.

### <a name="remarks"></a>Uwagi

`afxDump` Obiekt jest tworzony automatycznie.

Nie wpisuj do bazowego `CFile` w trakcie aktywnej; w przeciwnym razie kontekstu zrzutu będzie zakłócać zrzutu. W obszarze środowiska Windows, danych wyjściowych jest kierowany do debugera za pomocą funkcji Windows `OutputDebugString`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

##  <a name="dumpashex"></a>  CDumpContext::DumpAsHex

Zrzuca określonego typu w formacie liczb szesnastkowych.

```
CDumpContext& DumpAsHex(BYTE b);
CDumpContext& DumpAsHex(DWORD dw);
CDumpContext& DumpAsHex(int n);
CDumpContext& DumpAsHex(LONG l);
CDumpContext& DumpAsHex(LONGLONG n);
CDumpContext& DumpAsHex(UINT u);
CDumpContext& DumpAsHex(ULONGLONG n);
CDumpContext& DumpAsHex(WORD w);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CDumpContext` obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego do elementu o określonym typie jako liczbę szesnastkową zrzutu. Aby zrzutu tablicy, należy wywołać [CDumpContext::HexDump](#hexdump).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

##  <a name="flush"></a>  CDumpContext::Flush

Wymusza pozostałych buforów, które są zapisywane w pliku danych dołączona do kontekstu zrzutu.

```
void Flush();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

##  <a name="getdepth"></a>  CDumpContext::GetDepth

Określa, czy w procesie zrzutu głębokiego lub skrócona.

```
int GetDepth() const;
```

### <a name="return-value"></a>Wartość zwracana

Głębokość zrzutu zgodnie z ustawieniem `SetDepth`.

### <a name="example"></a>Przykład

  Zobacz przykład [SetDepth](#setdepth).

##  <a name="hexdump"></a>  CDumpContext::HexDump

Zrzuca tablicę bajtów w formacie liczb szesnastkowych.

```
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>Parametry

*lpszLine*<br/>
Ciąg służący do wypełniania wyjściowego na początku nowego wiersza.

*pby*<br/>
Wskaźnik do buforu zawierające bajty do zrzutu.

*nBytes*<br/>
Liczba bajtów do zrzutu.

*nWidth*<br/>
Maksymalna liczba bajtów zrzucany na wiersz (nie szerokość wiersza danych wyjściowych).

### <a name="remarks"></a>Uwagi

Aby zrzutu typem elementu jednej, określonej jako liczbę szesnastkową, należy wywołać [CDumpContext::DumpAsHex](#dumpashex).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

##  <a name="operator_lt_lt"></a>  CDumpContext::operator &lt;&lt;

Wyświetla określone dane do kontekstu zrzutu.

```
CDumpContext& operator<<(const CObject* pOb);
CDumpContext& operator<<(const CObject& ob);
CDumpContext& operator<<(LPCTSTR lpsz);
CDumpContext& operator<<(const void* lp);
CDumpContext& operator<<(BYTE by);
CDumpContext& operator<<(WORD w);
CDumpContext& operator<<(DWORD dw);
CDumpContext& operator<<(int n);
CDumpContext& operator<<(double d);
CDumpContext& operator<<(float f);
CDumpContext& operator<<(LONG l);
CDumpContext& operator<<(UINT u);
CDumpContext& operator<<(LPCWSTR lpsz);
CDumpContext& operator<<(LPCSTR lpsz);
CDumpContext& operator<<(LONGLONG n);
CDumpContext& operator<<(ULONGLONG n);
CDumpContext& operator<<(HWND h);
CDumpContext& operator<<(HDC h);
CDumpContext& operator<<(HMENU h);
CDumpContext& operator<<(HACCEL h);
CDumpContext& operator<<(HFONT h);
```

### <a name="return-value"></a>Wartość zwracana

A `CDumpContext` odwołania. Przy użyciu wartości zwracanej, można napisać wstawienia wielu w jednym wierszu kodu źródłowego.

### <a name="remarks"></a>Uwagi

Operator wstawiania jest przeciążony dla `CObject` wskaźniki także, jak w przypadku typów pierwotnych najbardziej. Wskaźnik do znaku skutkuje zrzut zawartości ciągu; wskaźnik do **void** skutkuje zrzut szesnastkowy tylko adresu. LONGLONG skutkuje zrzutu 64-bitowej podpisanej liczby całkowitej; ULONGLONG powoduje zrzut 64-bitowej nieoznaczonej liczby całkowitej.

Jeśli używasz IMPLEMENT_DYNAMIC lub IMPLEMENT_SERIAL — makro w implementacji klasy, a następnie operator wstawiania za pośrednictwem `CObject::Dump`, spowodują, że nazwa usługi `CObject`-klasy pochodnej. W przeciwnym razie zostanie wydrukowany `CObject`. Jeśli zastąpisz `Dump` funkcji klasy, wówczas może zapewnić bardziej opisowe danych wyjściowych obiektu zawartości zamiast zrzut szesnastkowy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

##  <a name="setdepth"></a>  CDumpContext::SetDepth

Ustawia głębię dla zrzutu.

```
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>Parametry

*nNewDepth*<br/>
Nowa wartość głębi.

### <a name="remarks"></a>Uwagi

Jeśli to zrzucanie typ pierwotny lub prostego `CObject` który nie zawiera żadnych wskaźników do innych obiektów, a następnie wartość 0 jest wystarczająca. Wartość większą niż 0 określa głębokiego zrzutu, w której wszystkie obiekty są zrzucany cyklicznie. Na przykład głębokiego zrzutu kolekcji będzie zrzut wszystkich elementów w kolekcji. Można użyć innych wartości głębokości określonych w swojej klasy pochodne.

> [!NOTE]
>  Odwołania cykliczne nie są wykrywane w zrzuty głębokości i może spowodować pętli nieskończonej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)
