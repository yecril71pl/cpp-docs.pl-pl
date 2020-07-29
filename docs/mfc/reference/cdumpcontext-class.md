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
ms.openlocfilehash: 3a81e06586e6de14d57ce4c4de36dc30c73383f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212517"
---
# <a name="cdumpcontext-class"></a>Klasa CDumpContext

Obsługuje dane wyjściowe diagnostyki zorientowane strumieniowo w postaci tekstu do odczytu przez człowieka.

## <a name="syntax"></a>Składnia

```
class CDumpContext
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDumpContext:: CDumpContext](#cdumpcontext)|Konstruuje `CDumpContext` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDumpContext::D umpAsHex](#dumpashex)|Zrzuca wskazany element w formacie szesnastkowym.|
|[CDumpContext:: Flush](#flush)|Opróżnia wszystkie dane w buforze kontekstu zrzutu.|
|[CDumpContext:: getgłębokości](#getdepth)|Pobiera liczbę całkowitą odpowiadającą głębokości zrzutu.|
|[CDumpContext:: HexDump](#hexdump)|Zrzuca bajty zawarte w tablicy w formacie szesnastkowym.|
|[CDumpContext:: setgłębokości](#setdepth)|Ustawia głębokość zrzutu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDumpContext:: operator&lt;&lt;](#operator_lt_lt)|Wstawia zmienne i obiekty do kontekstu zrzutu.|

## <a name="remarks"></a>Uwagi

`CDumpContext`nie ma klasy bazowej.

W przypadku większości dumpingu można użyć [afxDump](diagnostic-services.md#afxdump), wstępnie zadeklarowanego `CDumpContext` obiektu. `afxDump`Obiekt jest dostępny tylko w wersji Debug Biblioteka MFC.

Kilka z [usług diagnostycznych](../../mfc/reference/diagnostic-services.md) pamięci używa `afxDump` do ich danych wyjściowych.

W środowisku systemu Windows dane wyjściowe ze wstępnie zdefiniowanego `afxDump` obiektu, koncepcyjnie podobny do `cerr` strumienia, są kierowane do debugera za pośrednictwem funkcji systemu Windows `OutputDebugString` .

`CDumpContext`Klasa ma przeciążony operator wstawiania ( **<<** ) dla `CObject` wskaźników, które zrzucają dane obiektu. Jeśli potrzebujesz niestandardowego formatu zrzutu dla obiektu pochodnego, Przesłoń [CObject::D UMP](../../mfc/reference/cobject-class.md#dump). Większość klas Microsoft Foundation implementuje przesłoniętą `Dump` funkcję członkowską.

Klasy, które nie pochodzą z `CObject` , takie jak `CString` , `CTime` i `CTimeSpan` mają własne przeciążone `CDumpContext` Operatory wstawiania, tak jak często używane struktury, takie jak `CFileStatus` , `CPoint` i `CRect` .

Jeśli używasz makra [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) lub [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) w implementacji klasy, `CObject::Dump` zostanie wydrukowana nazwa `CObject` klasy pochodnej. W przeciwnym razie zostanie wydrukowany `CObject` .

`CDumpContext`Klasa jest dostępna zarówno dla wersji debugowania, jak i wersji biblioteki, ale `Dump` funkcja członkowska jest definiowana tylko w wersji do debugowania. Użyj instrukcji **#ifdef _DEBUG**  /  `#endif` , aby przeciągać kod diagnostyczny, łącznie z niestandardowymi `Dump` funkcjami składowymi.

Przed utworzeniem własnego obiektu należy `CDumpContext` utworzyć `CFile` obiekt, który służy jako miejsce docelowe zrzutu.

Aby uzyskać więcej informacji na temat `CDumpContext` , zobacz [debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CDumpContext`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>CDumpContext:: CDumpContext

Konstruuje obiekt klasy `CDumpContext` .

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Wskaźnik do `CFile` obiektu, który jest miejscem docelowym zrzutu.

### <a name="remarks"></a>Uwagi

`afxDump`Obiekt jest konstruowany automatycznie.

Nie zapisuj w źródłowym czasie, `CFile` gdy kontekst zrzutu jest aktywny; w przeciwnym razie będzie przeszkadzać w zrzucie. W środowisku systemu Windows dane wyjściowe są kierowane do debugera za pośrednictwem funkcji systemu Windows `OutputDebugString` .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpContext::D umpAsHex

Zrzuca określony typ sformatowany jako liczby szesnastkowe.

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

Wywołaj tę funkcję elementu członkowskiego, aby zrzucić element określonego typu jako liczbę szesnastkową. Aby zrzucić tablicę, wywołaj [CDumpContext:: hexdump](#hexdump).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a>CDumpContext:: Flush

Wymusza, aby wszystkie pozostałe dane w buforach były zapisywane do pliku dołączonego do kontekstu zrzutu.

```cpp
void Flush();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpContext:: getgłębokości

Określa, czy zrzut głębokiego lub płytki jest w toku.

```
int GetDepth() const;
```

### <a name="return-value"></a>Wartość zwracana

Głębokość zrzutu ustawiona przez `SetDepth` .

### <a name="example"></a>Przykład

  Zobacz przykład dla elementu [setgłębokości](#setdepth).

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a>CDumpContext:: HexDump

Zrzuca tablicę bajtów sformatowaną jako liczby szesnastkowe.

```cpp
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>Parametry

*lpszLine*<br/>
Ciąg do wyjścia na początku nowego wiersza.

*pby*<br/>
Wskaźnik do buforu zawierającego bajty do zrzutu.

*nBytes*<br/>
Liczba bajtów do zrzutu.

*nWidth*<br/>
Maksymalna liczba bajtów zrzucanych na wiersz (nie szerokość linii wyjściowej).

### <a name="remarks"></a>Uwagi

Aby zrzucić pojedynczy, konkretny typ elementu jako liczbę szesnastkową, wywołaj [CDumpContext::D umpashex](#dumpashex).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpContext:: operator&lt;&lt;

Wyprowadza określone dane do kontekstu zrzutu.

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

`CDumpContext`Odwołanie. Przy użyciu wartości zwracanej można napisać wiele wstawek w jednym wierszu kodu źródłowego.

### <a name="remarks"></a>Uwagi

Operator wstawiania jest przeciążony dla `CObject` wskaźników oraz dla większości typów pierwotnych. Wskaźnik do znaku powoduje zrzut treści ciągu; wskaźnik do **`void`** wyniku w szesnastkowym zrzucie tylko adresu. LONGLONG skutkuje zrzutem 64-bitowej liczby całkowitej ze znakiem; ULONGLONG skutkuje zrzutem 64-bitowej liczby całkowitej bez znaku.

W przypadku użycia makra IMPLEMENT_DYNAMIC lub IMPLEMENT_SERIAL w implementacji klasy, operator wstawiania, przez `CObject::Dump` , będzie drukował nazwę `CObject` klasy pochodnej. W przeciwnym razie zostanie wydrukowany `CObject` . Jeśli zastąpisz `Dump` funkcję klasy, możesz podać bardziej zrozumiały wynik zawartości obiektu zamiast zrzutu szesnastkowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a>CDumpContext:: setgłębokości

Ustawia głębokość zrzutu.

```cpp
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>Parametry

*nNewDepth*<br/>
Nowa wartość głębokości.

### <a name="remarks"></a>Uwagi

W przypadku zatopienia typu pierwotnego lub prostego `CObject` , który nie zawiera wskaźników do innych obiektów, wartość 0 jest wystarczająca. Wartość większa niż 0 określa zrzut głębokiego, w którym wszystkie obiekty są rekursywnie roztopione. Na przykład głębokie zrzut kolekcji spowoduje zrzut wszystkich elementów kolekcji. W klasach pochodnych można używać innych konkretnych wartości głębokości.

> [!NOTE]
> Odwołania cykliczne nie są wykrywane w przypadku zrzutów głębokiego i mogą powodować nieskończone pętle.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)
