---
title: Klasa CDumpContext | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
dev_langs: C++
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fe45f47520efd0a96dff9b31f18eb267d0058c61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdumpcontext-class"></a>Klasa CDumpContext
Obsługuje zorientowanych strumieniowo diagnostycznych danych wyjściowych w postaci tekstu zrozumiałą dla użytkownika.  
  
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
|[CDumpContext::DumpAsHex](#dumpashex)|Zrzuty element wskazany w formacie szesnastkowym.|  
|[CDumpContext::Flush](#flush)|Czyści wszystkie dane w buforze kontekstu zrzutu.|  
|[CDumpContext::GetDepth](#getdepth)|Pobiera całkowitą głębokość zrzutu.|  
|[CDumpContext::HexDump](#hexdump)|Zrzuty bajtów zawartych w tablicy w formacie szesnastkowym.|  
|[CDumpContext::SetDepth](#setdepth)|Ustawia głębię zrzutu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDumpContext::operator&lt;&lt;](#operator_lt_lt)|Wstawia zmiennych i obiektów w kontekście zrzutu.|  
  
## <a name="remarks"></a>Uwagi  
 `CDumpContext`nie ma klasy podstawowej.  
  
 Można użyć [afxdump —](diagnostic-services.md#afxdump), wcześniej zadeklarowanej `CDumpContext` obiektu większość zrzucanie sieci. `afxDump` Obiekt jest dostępny tylko w wersji do debugowania programu Microsoft Foundation Class Library.  
  
 Kilka pamięci [usługi diagnostyczne](../../mfc/reference/diagnostic-services.md) użyj `afxDump` dla swoich danych wyjściowych.  
  
 W środowisku systemu Windows, dane wyjściowe z wstępnie zdefiniowane `afxDump` obiektu podobny do `cerr` strumienia, są kierowane do debugera za pomocą funkcji Windows **OutputDebugString**.  
  
 `CDumpContext` Klasa ma przeciążone wstawiania (  **<<** ) operator `CObject` wskaźników, które zrzuty danych obiektu. Jeśli potrzebujesz formatu niestandardowego zrzutu dla obiekt pochodnej, Zastąp [CObject::Dump](../../mfc/reference/cobject-class.md#dump). Większość Microsoft Foundation classes implementacji przesłoniętych `Dump` funkcję elementu członkowskiego.  
  
 Klasy, które nie pochodzą z `CObject`, takich jak `CString`, `CTime`, i `CTimeSpan`, ma swoje własne przeciążone `CDumpContext` operatorów wstawiania, jak często używane struktury, takich jak **CFileStatus**, `CPoint`, i `CRect`.  
  
 Jeśli używasz [implement_dynamic —](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) lub [implement_serial —](../../mfc/reference/run-time-object-model-services.md#implement_serial) makra w implementacji klasy, a następnie `CObject::Dump` będzie drukować nazwę Twojej `CObject`-klasy. W przeciwnym razie będzie drukować `CObject`.  
  
 `CDumpContext` Klasy jest dostępny zarówno Debug i Release wersje biblioteki, ale `Dump` funkcja członkowska jest zdefiniowany tylko w wersji do debugowania. Użyj **#ifdef _DEBUG**  /  `#endif` instrukcje nawiasów diagnostyki kodu, w tym niestandardowe `Dump` funkcji elementów członkowskich.  
  
 Przed utworzeniem własnych `CDumpContext` obiektu, należy utworzyć `CFile` obiekt, który służy jako miejsce docelowe zrzutu.  
  
 Aby uzyskać więcej informacji na temat `CDumpContext`, zobacz [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
 **#define _DEBUG**  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CDumpContext`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="cdumpcontext"></a>CDumpContext::CDumpContext  
 Tworzy obiekt klasy `CDumpContext`.  
  
```  
CDumpContext(CFile* pFile = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pFile`  
 Wskaźnik do `CFile` obiekt, który jest miejscem docelowym zrzutu.  
  
### <a name="remarks"></a>Uwagi  
 `afxDump` Obiekt jest tworzony automatycznie.  
  
 Nie zapisuj odpowiadającego `CFile` kontekstu zrzutu jest aktywne, a w przeciwnym, będzie zakłócać zrzutu. W środowisku systemu Windows, dane wyjściowe jest kierowany do debugera za pomocą funkcji Windows **OutputDebugString**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]  
  
##  <a name="dumpashex"></a>CDumpContext::DumpAsHex  
 Zrzuty określonego typu sformatowane jako szesnastkowe.  
  
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
 Wywołanie tej funkcji Członkowskich do zrzutu elementu określonego typu jako liczbę szesnastkową. Aby zrzutu tablicy, należy wywołać [CDumpContext::HexDump](#hexdump).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]  
  
##  <a name="flush"></a>CDumpContext::Flush  
 Wymusza pozostałych buforów są zapisywane w pliku danych dołączona do kontekstu zrzutu.  
  
```  
void Flush();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]  
  
##  <a name="getdepth"></a>CDumpContext::GetDepth  
 Określa, czy zrzutu bezpośrednich lub skrócona jest w toku.  
  
```  
int GetDepth() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Głębokość zrzutu zgodnie z ustawieniami `SetDepth`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [SetDepth](#setdepth).  
  
##  <a name="hexdump"></a>CDumpContext::HexDump  
 Zrzuty tablicy bajtów w formacie szesnastkowe.  
  
```  
void HexDump(
    LPCTSTR lpszLine,  
    BYTE* pby,  
    int nBytes,  
    int nWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszLine*  
 Ciąg do wyjściowego na początku nowego wiersza.  
  
 *pby*  
 Wskaźnik do buforu zawierająca bajty do zrzutu.  
  
 `nBytes`  
 Liczba bajtów do zrzutu.  
  
 `nWidth`  
 Maksymalna liczba bajtów utworzyć zrzutu w jednym wierszu (nie szerokość wiersza danych wyjściowych).  
  
### <a name="remarks"></a>Uwagi  
 Aby zrzutu typu elementu jednej, określonej jako liczbę szesnastkową, należy wywołać [CDumpContext::DumpAsHex](#dumpashex).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]  
  
##  <a name="operator_lt_lt"></a>CDumpContext::operator&lt;&lt;  
 Dane wyjściowe określone dane w kontekście zrzutu.  
  
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
 A `CDumpContext` odwołania. Przy użyciu wartości zwracanej, może zapisywać wiele wstawienia w jednym wierszu kodu źródłowego.  
  
### <a name="remarks"></a>Uwagi  
 Operator wstawiania jest przeciążony dla `CObject` wskaźniki również, jak w przypadku typów pierwotnych najbardziej. Wskaźnik do znaku powoduje zrzutu zawartości ciągu; wskaźnik do `void` powoduje szesnastkowe zrzut tylko adresu. A **LONGLONG** powoduje zrzutu 64-bitowych podpisane liczby całkowite; A **ULONGLONG** powoduje zrzutu 64-bitowej liczby całkowitej bez znaku.  
  
 Jeśli używasz `IMPLEMENT_DYNAMIC` lub `IMPLEMENT_SERIAL` makra w implementacji klasy, a następnie operator wstawiania za pośrednictwem `CObject::Dump`, będzie drukować nazwę Twojej `CObject`-klasy. W przeciwnym razie będzie drukować `CObject`. Jeśli można zastąpić `Dump` funkcji klasy, wówczas może zapewnić bardziej zrozumiałej dane wyjściowe obiektu treści zamiast zrzutu szesnastkową.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]  
  
##  <a name="setdepth"></a>CDumpContext::SetDepth  
 Ustawia głębokość dla zrzutu.  
  
```  
void SetDepth(int nNewDepth);
```  
  
### <a name="parameters"></a>Parametry  
 *nNewDepth*  
 Nowa wartość głębokość.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli są zrzucanie typem pierwotnym lub prostego `CObject` zawierający nie wskaźników do innych obiektów, a następnie wartość 0 jest wystarczająca. Wartość większą niż 0 określa zrzutu bezpośrednich, których wszystkie obiekty są utworzyć zrzutu rekursywnie. Na przykład zrzutu bezpośrednich kolekcji zostanie zrzut wszystkich elementów w kolekcji. Inne wartości określonych głębokość można używać w sieci klas pochodnych.  
  
> [!NOTE]
>  Odwołania cykliczne nie są wykrywane w bezpośrednich zrzutów i może powodować nieskończone pętle.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cfile — klasa](../../mfc/reference/cfile-class.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)
