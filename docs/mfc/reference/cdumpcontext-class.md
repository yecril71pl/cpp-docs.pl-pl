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
ms.openlocfilehash: e89bbc5f263dc9303140e43914619090109b8315
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753209"
---
# <a name="cdumpcontext-class"></a>Klasa CDumpContext

Obsługuje dane wyjściowe diagnostyczne zorientowane na strumień w postaci tekstu czytelnego dla człowieka.

## <a name="syntax"></a>Składnia

```
class CDumpContext
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDumpContext::CDumpContext](#cdumpcontext)|Konstruuje `CDumpContext` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDumpContext::DumpAsHex](#dumpashex)|Zrzuca wskazany element w formacie szesnastkowym.|
|[CDumpContext::Opróżnianie](#flush)|Opróżnia wszystkie dane w buforze kontekstu zrzutu.|
|[CDumpContext::GetDepth](#getdepth)|Pobiera liczbę całkowitą odpowiadającą głębokości zrzutu.|
|[CDumpContext::HexDump](#hexdump)|Zrzutów bajtów zawartych w tablicy w formacie szesnastkowym.|
|[CDumpContext::SetDepth](#setdepth)|Ustawia głębokość zrzutu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDumpContext::operator&lt;&lt;](#operator_lt_lt)|Wstawia zmienne i obiekty do kontekstu zrzutu.|

## <a name="remarks"></a>Uwagi

`CDumpContext`nie ma klasy podstawowej.

Możesz użyć [afxDump](diagnostic-services.md#afxdump), wstępnie `CDumpContext` zadeklarowanego obiektu, dla większości dumpingu. Obiekt `afxDump` jest dostępny tylko w wersji debugowania biblioteki klas programu Microsoft Foundation.

Kilka usług [diagnostycznych](../../mfc/reference/diagnostic-services.md) `afxDump` pamięci używać do ich danych wyjściowych.

W środowisku systemu Windows dane wyjściowe `afxDump` ze wstępnie zdefiniowanego `cerr` obiektu, koncepcyjnie podobne do `OutputDebugString`strumienia, są kierowane do debugera za pośrednictwem funkcji systemu Windows .

Klasa `CDumpContext` ma przeciążony operator wstawiania ( **<<**) dla `CObject` wskaźników, które zrzuca dane obiektu. Jeśli potrzebujesz niestandardowego formatu zrzutu dla obiektu pochodnego, należy zastąpić [CObject::Dump](../../mfc/reference/cobject-class.md#dump). Większość klas programu Microsoft Foundation `Dump` implementuje zastąpioną funkcję elementu członkowskiego.

Klasy, które nie `CObject`są pochodną `CTime`, `CTimeSpan`takich jak `CString`, `CDumpContext` i , mają własne przeciążone operatory wstawiania, podobnie jak często używane struktury, takie jak `CFileStatus`, `CPoint`i `CRect`.

Jeśli użyjesz [makra IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) lub [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) w implementacji klasy, spowoduje `CObject::Dump` wydrukowanie `CObject`nazwy klasy pochodnej. W przeciwnym razie `CObject`zostanie wydrukowany plik .

Klasa `CDumpContext` jest dostępna zarówno w wersji debugowania i `Dump` wydania biblioteki, ale funkcja elementu członkowskiego jest zdefiniowana tylko w wersji debugowania. Użyj **instrukcji #ifdef _DEBUG,**  /  `#endif` aby zassmować kod `Dump` diagnostyczny, w tym niestandardowe funkcje członkowskie.

Przed utworzeniem `CDumpContext` własnego obiektu należy `CFile` utworzyć obiekt, który służy jako miejsce docelowe zrzutu.

Aby uzyskać `CDumpContext`więcej informacji na temat , zobacz [Debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CDumpContext`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>CDumpContext::CDumpContext

Konstruuje obiekt `CDumpContext`klasy .

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>Parametry

*p Plik*<br/>
Wskaźnik do `CFile` obiektu, który jest miejscem docelowym zrzutu.

### <a name="remarks"></a>Uwagi

Obiekt `afxDump` jest konstruowany automatycznie.

Nie zapisuj `CFile` do podstawowej, gdy kontekst zrzutu jest aktywny; w przeciwnym razie będzie kolidować z wysypiskiem. W środowisku systemu Windows dane wyjściowe są kierowane `OutputDebugString`do debugera za pośrednictwem funkcji systemu Windows .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpContext::DumpAsHex

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

Wywołanie tej funkcji elementu członkowskiego, aby zrzucić element określonego typu jako numer szesnastkowy. Aby zrzucić tablicę, wywołanie [CDumpContext::HexDump](#hexdump).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a>CDumpContext::Opróżnianie

Wymusza wszystkie dane pozostające w buforach do zapisania w pliku dołączonym do kontekstu zrzutu.

```cpp
void Flush();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpContext::GetDepth

Określa, czy głęboki lub płytki zrzut jest w trakcie procesu.

```
int GetDepth() const;
```

### <a name="return-value"></a>Wartość zwracana

Głębokość zrzutu ustawiona `SetDepth`przez .

### <a name="example"></a>Przykład

  Zobacz przykład [setDepth](#setdepth).

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a>CDumpContext::HexDump

Zrzuca tablicę bajtów sformatowanych jako liczby szesnastkowe.

```cpp
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>Parametry

*lpszLine (linia lpszLine)*<br/>
Ciąg wyjściowy na początku nowego wiersza.

*pby (polski)*<br/>
Wskaźnik do buforu zawierającego bajty do zrzutu.

*n Bajty*<br/>
Liczba bajtów do zrzucenia.

*nWidth (ww.*<br/>
Maksymalna liczba bajtów po cenach dumpingowych na linię (a nie szerokość linii wyjściowej).

### <a name="remarks"></a>Uwagi

Aby zrzucić pojedynczy, określony typ elementu jako numer szesnastkowy, zadzwoń [do CDumpContext::DumpAsHex](#dumpashex).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpContext::operator&lt;&lt;

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

Odwołanie. `CDumpContext` Za pomocą zwracanej wartości można zapisać wiele wstawień w jednym wierszu kodu źródłowego.

### <a name="remarks"></a>Uwagi

Operator wstawiania jest `CObject` przeciążony dla wskaźników, a także dla większości typów pierwotnych. Wskaźnik do znaku powoduje zrzut zawartości ciągu; wskaźnik do **void** powoduje szesnastkowe zrzutu adresu tylko. Longlong powoduje zrzut 64-bitowej liczby całkowitej podpisanej; ULONGLONG powoduje zrzut 64-bitowej niepodpisanej liczby całkowitej.

Jeśli użyjesz makra IMPLEMENT_DYNAMIC lub IMPLEMENT_SERIAL w implementacji klasy, operator wstawiania, za `CObject::Dump`pośrednictwem `CObject`, wydrukuje nazwę klasy pochodnej. W przeciwnym razie `CObject`zostanie wydrukowany plik . Jeśli zastąpisz `Dump` funkcję klasy, możesz podać bardziej znaczące dane wyjściowe zawartości obiektu zamiast zrzutu szesnastkowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a>CDumpContext::SetDepth

Ustawia głębokość dla zrzutu.

```cpp
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>Parametry

*nNewDepth*<br/>
Nowa wartość głębokości.

### <a name="remarks"></a>Uwagi

Jeśli są dumpingu typu pierwotnego `CObject` lub proste, który nie zawiera żadnych wskaźników do innych obiektów, a następnie wartość 0 jest wystarczająca. Wartość większa niż 0 określa głęboki zrzut, w którym wszystkie obiekty są po cenach dumpingowych cyklicznie. Na przykład głębokie zrzutu kolekcji zrzuci wszystkie elementy kolekcji. Można użyć innych określonych wartości głębokości w klasach pochodnych.

> [!NOTE]
> Odwołania cykliczne nie są wykrywane w głębokich zrzutach i mogą powodować nieskończone pętle.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)
