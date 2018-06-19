---
title: Klasa CAtlArray | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ceeaf5250cc9dc5cb4cb25c47b3fe179c7c5295
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365559"
---
# <a name="catlarray-class"></a>Klasa CAtlArray
Ta klasa implementuje tablicy obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```  
  
#### <a name="parameters"></a>Parametry  
 *E*  
 Typ danych, które mają być przechowywane w tablicy.  
  
 *ETraits*  
 Kod używany do kopiowania lub przenoszenia elementów.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Dodaj](#add)|Wywołaj tę metodę w celu dodania elementu do obiektu array.|  
|[Dołącz](#append)|Wywołanie tej metody, aby dodać do końca innej zawartości tablicy.|  
|[AssertValid](#assertvalid)|Wywołanie tej metody, aby upewnić się, że obiekt tablicy jest prawidłowy.|  
|[CAtlArray](#catlarray)|Konstruktor.|  
|[~ CAtlArray](#dtor)|Destruktor.|  
|[Kopiuj](#copy)|Wywołanie tej metody można kopiować elementy tablicy jednego do drugiego.|  
|[FreeExtra](#freeextra)|Wywołaj tę metodę, aby usunąć wszelkie puste elementy z tablicy.|  
|[GetAt](#getat)|Wywołaj tę metodę, aby pobrać jeden element z obiektu tablicy.|  
|[GetCount](#getcount)|Wywołaj tę metodę, aby zwrócić liczby elementy przechowywane w tablicy.|  
|[GetData](#getdata)|Wywołaj tę metodę w celu zwraca wskaźnik do pierwszego elementu w tablicy.|  
|[InsertArrayAt](#insertarrayat)|Wywołanie tej metody, aby wstawić jedną tablicę do innego.|  
|[InsertAt](#insertat)|Wywołaj tę metodę, aby wstawić nowego elementu (lub wiele kopii elementu) w obiekcie tablicy.|  
|[IsEmpty](#isempty)|Wywołanie tej metody, aby sprawdzić, czy tablica jest pusta.|  
|[RemoveAll](#removeall)|Wywołaj tę metodę, aby usunąć wszystkie elementy z obiektu array.|  
|[Element RemoveAt](#removeat)|Wywołaj tę metodę, aby usunąć co najmniej jednego elementu z tablicy.|  
|[SetAt](#setat)|Wywołanie tej metody można ustawić wartości elementu w obiekcie tablicy.|  
|[SetAtGrow](#setatgrow)|Wywołaj tę metodę, aby ustawić wartość elementu w obiekcie tablicy, rozszerzanie tablicy zgodnie z potrzebami.|  
|[SetCount](#setcount)|Wywołaj tę metodę, aby ustawić rozmiar obiektu tablicy.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator&#91;&#93;](#operator_at)|Wywołanie tego operatora zwraca odwołanie do elementu w tablicy.|  

  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[INARGTYPE](#inargtype)|Typ danych służących do dodawania elementów do tablicy.|  
|[OUTARGTYPE](#outargtype)|Typ danych używany do pobierania elementów z tablicy.|  
  
## <a name="remarks"></a>Uwagi  
 **CAtlArray** udostępnia metody do tworzenia i zarządzania tablicę elementów typu zdefiniowanego przez użytkownika. Mimo że jest to podobne do tablic C standard, **CAtlArray** obiektu dynamicznie można zmniejszyć rozmiar i wzrostu w razie potrzeby. Indeks tablicy zawsze rozpoczyna się na pozycji 0, a górną granicę można stałe, lub można rozwinąć w miarę dodawania nowych elementów.  
  
 Dla tablic z mniejszą liczbą elementów klasy ATL [CSimpleArray](../../atl/reference/csimplearray-class.md) mogą być używane.  
  
 **CAtlArray** jest ściśle powiązana z MFC **carray —** klasy i będzie działać w projekcie MFC, choć bez obsługi serializacji.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
##  <a name="add"></a>  CAtlArray::Add  
 Wywołaj tę metodę w celu dodania elementu do obiektu array.  
  
```
size_t Add(INARGTYPE element);
size_t Add();
```  
  
### <a name="parameters"></a>Parametry  
 `element`  
 Element, który ma zostać dodany do tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca indeks elementu dodany.  
  
### <a name="remarks"></a>Uwagi  
 Nowy element zostanie dodany do końca tablicy. Jeśli nie ma żadnego elementu pod warunkiem dodaniu pustego elementu; oznacza to, że tablicy zwiększa się rozmiar tak, jakby został dodany element prawdziwe. W przypadku niepowodzenia operacji [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) jest wywoływana z argumentem E_OUTOFMEMORY.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]  
  
##  <a name="append"></a>  CAtlArray::Append  
 Wywołanie tej metody, aby dodać do końca innej zawartości tablicy.  
  
```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `aSrc`  
 Tablica, która ma zostać dołączony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca indeks pierwszego elementu dołączany.  
  
### <a name="remarks"></a>Uwagi  
 Elementy w podanej tablicy są dodawane na końcu istniejącej tablicy. W razie potrzeby będzie można przydzielić pamięci w celu uwzględnienia nowych elementów.  
  
 Tablice muszą być tego samego typu, a nie jest możliwe do dołączenia tablicy do samej siebie.  
  
 W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `CAtlArray` argument nie jest prawidłową tablicy lub, jeśli `aSrc` odwołuje się do tego samego obiektu. Nieprawidłowe argumenty w kompilacjach wydania może spowodować nieprzewidywalne zachowanie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]  
  
##  <a name="assertvalid"></a>  CAtlArray::AssertValid  
 Wywołanie tej metody, aby upewnić się, że obiekt tablicy jest prawidłowy.  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekt tablicy nie jest prawidłowy, `ATLASSERT` zgłosi potwierdzenia. Ta metoda jest dostępna tylko wtedy, gdy zdefiniowano _DEBUG.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]  
  
##  <a name="catlarray"></a>  CAtlArray::CAtlArray  
 Konstruktor.  
  
```
CAtlArray() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje obiekt array.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]  
  
##  <a name="dtor"></a>  CAtlArray:: ~ CAtlArray  
 Destruktor.  
  
```
~CAtlArray() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszelkie zasoby używane przez obiekt array.  
  
##  <a name="copy"></a>  CAtlArray::Copy  
 Wywołanie tej metody można kopiować elementy tablicy jednego do drugiego.  
  
```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `aSrc`  
 Źródło elementów, aby skopiować do tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby zastąpić elementów co tablica elementów innej tablicy. W razie potrzeby będzie można przydzielić pamięci w celu uwzględnienia nowych elementów. Nie jest możliwe kopiowanie elementów tablicy do samej siebie.  
  
 Jeśli ma zostać zachowana istniejącą zawartość elementu tablicy, użyj [CAtlArray::Append](#append) zamiast tego.  
  
 W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli istniejące `CAtlArray` obiekt nie jest prawidłowa, lub jeśli `aSrc` odwołuje się do tego samego obiektu. Nieprawidłowe argumenty w kompilacjach wydania może spowodować nieprzewidywalne zachowanie.  
  
> [!NOTE]
> `CAtlArray::Copy` nie obsługuje tablic składające się z utworzonych z elementów [CAutoPtr](../../atl/reference/cautoptr-class.md) klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]  
  
##  <a name="freeextra"></a>  CAtlArray::FreeExtra  
 Wywołaj tę metodę, aby usunąć wszelkie puste elementy z tablicy.  
  
```
void FreeExtra() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wszelkie puste elementy są usuwane, ale rozmiar i górna granica tablicy pozostają niezmienione.  
  
 W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli obiekt CAtlArray jest nieprawidłowy lub tablica może spowodować przekroczenie maksymalnego rozmiaru.  
  
##  <a name="getat"></a>  CAtlArray::GetAt  
 Wywołanie, że tę metodę w celu pobiera jeden element z obiektu array.  
  
```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Wartość indeksu elementu tablicy do zwrócenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do elementu tablicy wymagane.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `iElement` przekracza liczbę elementów w tablicy. Nieprawidłowy argument w kompilacjach wydania może spowodować nieprzewidywalne zachowanie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]  
  
##  <a name="getcount"></a>  CAtlArray::GetCount  
 Wywołaj tę metodę, aby zwrócić liczby elementy przechowywane w tablicy.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę elementów przechowywane w tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy element w tablicy jest dostępna na pozycji 0, wartość zwracana przez `GetCount` ma zawsze numer 1 większa niż największa wartość indeksu.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlArray::GetAt](#getat).  
  
##  <a name="getdata"></a>  CAtlArray::GetData  
 Wywołaj tę metodę w celu zwraca wskaźnik do pierwszego elementu w tablicy.  
  
```
E* GetData() throw();
const E* GetData() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do lokalizacji pamięci przechowywania pierwszego elementu w tablicy. Jeśli elementy nie są dostępne, zostanie zwrócona wartość NULL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]  
  
##  <a name="inargtype"></a>  CAtlArray::INARGTYPE  
 Typ danych służących do dodawania elementów do tablicy.  
  
```
typedef ETraits::INARGTYPE INARGTYPE;
```  
  
##  <a name="insertarrayat"></a>  CAtlArray::InsertArrayAt  
 Wywołanie tej metody, aby wstawić jedną tablicę do innego.  
  
```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```  
  
### <a name="parameters"></a>Parametry  
 `iStart`  
 Indeks, jaką tablica jest do wstawienia.  
  
 `paNew`  
 Tablica do wstawienia.  
  
### <a name="remarks"></a>Uwagi  
 Elementy z tablicy `paNew` są kopiowane do obiektu tablicy, zaczynając od elementu `iStart`. Istniejące elementy tablicy są przenoszone w celu uniknięcia zastąpieniem.  
  
 W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `CAtlArray` obiekt nie jest prawidłowa, lub jeśli `paNew` wskaźnika jest wartością NULL lub jest nieprawidłowy.  
  
> [!NOTE]
> `CAtlArray::InsertArrayAt` nie obsługuje tablic składające się z utworzonych z elementów [CAutoPtr](../../atl/reference/cautoptr-class.md) klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]  
  
##  <a name="insertat"></a>  CAtlArray::InsertAt  
 Wywołaj tę metodę, aby wstawić nowego elementu (lub wiele kopii elementu) w obiekcie tablicy.  
  
```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Indeks, w którym element lub elementy mają zostać wstawione.  
  
 `element`  
 Wartość elementu lub elementów do wstawienia.  
  
 `nCount`  
 Liczba elementów do dodania.  
  
### <a name="remarks"></a>Uwagi  
 Wstawia jedną lub więcej elementów do tablicy, zaczynając od indeksu `iElement`. Istniejące elementy zostaną przeniesione do uniknięcia zastąpieniem.  
  
 W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `CAtlArray` obiektu jest nieprawidłowa, liczba elementów do dodania wynosi zero lub łączna liczba elementów jest za duża dla tablicy, tak aby zawierać. W kompilacjach sprzedaży detalicznej nieprawidłowe parametry przekazywania może spowodować nieoczekiwane wyniki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]  
  
##  <a name="isempty"></a>  CAtlArray::IsEmpty  
 Wywołanie tej metody, aby sprawdzić, czy tablica jest pusta.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli tablica jest pusta, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Tablica jest określany jako pustą, jeśli go nie zawiera żadnych elementów. W związku z tym nawet jeśli tablica zawiera puste elementy, nie jest pusty.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]  
  
##  <a name="operator_at"></a>  [CAtlArray::operator]  
 Wywołanie tego operatora zwraca odwołanie do elementu w tablicy.  
  
```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Wartość indeksu elementu tablicy do zwrócenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do elementu tablicy wymagane.  
  
### <a name="remarks"></a>Uwagi  
 Pełni podobną funkcję do [CAtlArray::GetAt](#getat). W odróżnieniu od klasy MFC [carray —](../../mfc/reference/carray-class.md), nie można użyć tego operatora w zastępstwie [CAtlArray::SetAt](#setat).  
  
 W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `iElement` przekracza całkowitą liczbę elementów w tablicy. W kompilacjach detalicznej nieprawidłowy parametr może spowodować nieoczekiwane wyniki.  
  
##  <a name="outargtype"></a>  CAtlArray::OUTARGTYPE  
 Typ danych używany do pobierania elementów z tablicy.  
  
```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```  
  
##  <a name="removeall"></a>  CAtlArray::RemoveAll  
 Wywołaj tę metodę, aby usunąć wszystkie elementy z obiektu array.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Usuwa wszystkie elementy z obiektu array.  
  
 Ta metoda wywołuje [CAtlArray::SetCount](#setcount) zmiany rozmiaru tablicy, a następnie zwalnia wszelkie alokacji pamięci.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlArray::IsEmpty](#isempty).  
  
##  <a name="removeat"></a>  CAtlArray::RemoveAt  
 Wywołaj tę metodę, aby usunąć co najmniej jednego elementu z tablicy.  
  
```
void RemoveAt(size_t iElement, size_t nCount = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Indeks pierwszego elementu do usunięcia.  
  
 `nCount`  
 Liczba elementów do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Usuwa co najmniej jednego elementu z tablicy. Wszystkie pozostałe elementy są przesuwane w dół. Górna granica jest zmniejszana, ale pamięci nie jest zwalniane do wywołania [CAtlArray::FreeExtra](#freeextra) staje się.  
  
 W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `CAtlArray` obiekt nie jest prawidłowa, lub, jeśli łączna liczba `iElement` i `nCount` przekracza całkowitą liczbę elementów w tablicy. W kompilacjach sprzedaży detalicznej nieprawidłowe parametry może spowodować nieoczekiwane wyniki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]  
  
##  <a name="setat"></a>  CAtlArray::SetAt  
 Wywołanie tej metody można ustawić wartości elementu w obiekcie tablicy.  
  
```
void SetAt(size_t iElement, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Indeks wskazanie do elementu tablicy można ustawić.  
  
 `element`  
 Nowa wartość określonego elementu.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `iElement` przekracza liczbę elementów w tablicy. Nieprawidłowy parametr w kompilacjach sprzedaży detalicznej, może spowodować nieoczekiwane wyniki.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlArray::GetAt](#getat).  
  
##  <a name="setcount"></a>  CAtlArray::SetCount  
 Wywołaj tę metodę, aby ustawić rozmiar obiektu tablicy.  
  
```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```  
  
### <a name="parameters"></a>Parametry  
 `nNewSize`  
 Wymagany rozmiar tablicy.  
  
 `nGrowBy`  
 Wartość używana do określenia wielkość bufora. Wartość -1 powoduje, że wewnętrznie obliczonej wartości do użycia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli tablica jest pomyślnie zmieniony, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Można zwiększyć lub zmniejszyć rozmiar tablicy. Po zwiększeniu, bardzo puste elementy są dodawane do tablicy. Jeśli zmniejszyć, zostaną usunięte elementy z największych indeksami i zwolnienie pamięci.  
  
 Ta metoda umożliwia ustawienie rozmiaru tablicy przed jego użyciem. Jeśli `SetCount` nie jest używany, proces dodawania elementów — i wykonać alokacji pamięci kolejnych — zmniejsza wydajność i fragmentu pamięci.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlArray::GetData](#getdata).  
  
##  <a name="setatgrow"></a>  CAtlArray::SetAtGrow  
 Wywołaj tę metodę, aby ustawić wartość elementu w obiekcie tablicy, rozszerzanie tablicy zgodnie z potrzebami.  
  
```
void SetAtGrow(size_t iElement, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parametry  
 `iElement`  
 Indeks wskazanie do elementu tablicy można ustawić.  
  
 `element`  
 Nowa wartość określonego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Zamienia wartość elementu wskazywanej przez indeks. Jeśli `iElement` jest większy niż bieżący rozmiar tablicy, tablicy jest automatycznie zwiększana przy użyciu wywołania do [CAtlArray::SetCount](#setcount). W kompilacjach do debugowania ATLASSERT zostanie wygenerowany, jeśli `CAtlArray` obiekt jest nieprawidłowy. W kompilacjach sprzedaży detalicznej nieprawidłowe parametry może spowodować nieoczekiwane wyniki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MMXSwarm](../../visual-cpp-samples.md)   
 [Przykładowe DynamicConsumer](../../visual-cpp-samples.md)   
 [Przykładowe UpdatePV](../../visual-cpp-samples.md)   
 [Przykładowe ramki](../../visual-cpp-samples.md)   
 [Carray — klasa](../../mfc/reference/carray-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
