---
title: "Carray — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CArray
- AFXTEMPL/CArray
- AFXTEMPL/CArray::CArray
- AFXTEMPL/CArray::Add
- AFXTEMPL/CArray::Append
- AFXTEMPL/CArray::Copy
- AFXTEMPL/CArray::ElementAt
- AFXTEMPL/CArray::FreeExtra
- AFXTEMPL/CArray::GetAt
- AFXTEMPL/CArray::GetCount
- AFXTEMPL/CArray::GetData
- AFXTEMPL/CArray::GetSize
- AFXTEMPL/CArray::GetUpperBound
- AFXTEMPL/CArray::InsertAt
- AFXTEMPL/CArray::IsEmpty
- AFXTEMPL/CArray::RemoveAll
- AFXTEMPL/CArray::RemoveAt
- AFXTEMPL/CArray::SetAt
- AFXTEMPL/CArray::SetAtGrow
- AFXTEMPL/CArray::SetSize
dev_langs: C++
helpviewer_keywords:
- CArray [MFC], CArray
- CArray [MFC], Add
- CArray [MFC], Append
- CArray [MFC], Copy
- CArray [MFC], ElementAt
- CArray [MFC], FreeExtra
- CArray [MFC], GetAt
- CArray [MFC], GetCount
- CArray [MFC], GetData
- CArray [MFC], GetSize
- CArray [MFC], GetUpperBound
- CArray [MFC], InsertAt
- CArray [MFC], IsEmpty
- CArray [MFC], RemoveAll
- CArray [MFC], RemoveAt
- CArray [MFC], SetAt
- CArray [MFC], SetAtGrow
- CArray [MFC], SetSize
ms.assetid: fead8b00-4cfd-4625-ad0e-251df62ba92f
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4087cfb584059923e4e05620c1f33d3cc11c3bd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="carray-class"></a>Carray — klasa
Obsługuje tablic, które są podobne do tablic C, ale dynamicznie pozwala zmniejszyć i wzrostu w razie potrzeby.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class TYPE, class ARG_TYPE = const TYPE&>  
class CArray : public CObject  
```  
  
#### <a name="parameters"></a>Parametry  
 `TYPE`  
 Parametr szablonu, który określa typ obiekty przechowywane w tablicy. `TYPE`jest parametrem, który jest zwracany przez `CArray`.  
  
 `ARG` *_* `TYPE`  
 Parametr szablonu, który określa typ argumentu, który umożliwia dostęp do obiektów przechowywanych w tablicy. Często odwołanie do `TYPE`. `ARG_TYPE`jest to parametr przekazywany do `CArray`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CArray::CArray](#carray)|Tworzy pustą tablicę.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CArray::Add](#add)|Dodaje element do końca tablicy; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CArray::Append](#append)|Dołącza innej tablicy do tablicy; rozwoju tablicy, w razie potrzeby|  
|[CArray::Copy](#copy)|Kopiuje innej tablicy do tablicy; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CArray::ElementAt](#elementat)|Zwraca tymczasowego odwołanie do wskaźnika elementu w tablicy.|  
|[CArray::FreeExtra](#freeextra)|Zwalnia wszystkie nieużywanej pamięci powyżej bieżącego górną granicę.|  
|[CArray::GetAt](#getat)|Zwraca wartość pod danym indeksem.|  
|[CArray::GetCount](#getcount)|Pobiera liczbę elementów w tej macierzy.|  
|[CArray::GetData](#getdata)|Umożliwia dostęp do elementów w tablicy. Może być **NULL**.|  
|[CArray::GetSize](#getsize)|Pobiera liczbę elementów w tej macierzy.|  
|[CArray::GetUpperBound](#getupperbound)|Zwraca największy nieprawidłowy indeks.|  
|[CArray::InsertAt](#insertat)|Wstawia elementu (lub wszystkie elementy w innej tablicy) od określonego indeksu.|  
|[CArray::IsEmpty](#isempty)|Określa, czy tablica jest pusta.|  
|[CArray::RemoveAll](#removeall)|Usuwa wszystkie elementy z tej tablicy.|  
|[CArray::RemoveAt](#removeat)|Usuwa element pod określonym indeksem.|  
|[CArray::SetAt](#setat)|Ustawia wartość dla danego indeksu; Tablica nie może wzrosnąć.|  
|[CArray::SetAtGrow](#setatgrow)|Ustawia wartość dla danego indeksu; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CArray::SetSize](#setsize)|Ustawia liczbę elementów, które mają zostać zawarte w tej macierzy.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator &#91; &#93;](#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|  
  
## <a name="remarks"></a>Uwagi  
 Indeksy tablicy zawsze rozpoczynają się od pozycji 0. Można wybrać, czy do naprawienia górna granica lub Włącz tablicy, tak aby rozwinąć po dodaniu elementów poza bieżącą powiązany. Jest przydzielana pamięć ciągłym górnej granicy, nawet jeśli niektóre elementy mają wartość null.  
  
> [!NOTE]
>  Większości metod, które zmiany rozmiaru `CArray` obiektu lub Dodaj elementy, aby go użyć [memcpy_s —](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md) można przenieść elementów. Jest to problem, ponieważ `memcpy_s` nie jest zgodny z wszystkie obiekty, które wymagają konstruktora do wywołania. Jeśli elementy `CArray` nie są zgodne z `memcpy_s`, należy utworzyć nowy `CArray` odpowiedniego rozmiaru. Następnie należy użyć [CArray::Copy](#copy) i [CArray::SetAt](#setat) do wypełnienia nowej tablicy, ponieważ te metody, użyj operatora przypisania zamiast `memcpy_s`.  
  
 Za pomocą tablicy C, czas dostępu dla `CArray` indeksowanego elementu jest stała i nie zależy od rozmiaru tablicy.  
  
> [!TIP]
>  Przed rozpoczęciem korzystania z tablicy, użyj [SetSize](#setsize) jego rozmiar i przydzielić pamięci dla niego. Jeśli nie używasz `SetSize`, dodawanie elementów do macierzy powoduje jego przydzielić często i skopiować. Częste zmiany alokacji i kopiowanie są mało wydajne i można fragmentu pamięci.  
  
 Jeśli potrzebujesz zrzutu poszczególnych elementów w tablicy, należy ustawić głębokość [CDumpContext](../../mfc/reference/cdumpcontext-class.md) obiektu 1 lub większą.  
  
 Niektóre funkcje Członkowskie wywołanie klasy funkcje globalne pomocy, które muszą być dostosowane dla większości zastosowań `CArray` klasy. Zobacz temat [pomocnicy klasy kolekcji](../../mfc/reference/collection-class-helpers.md) w sekcji makr MFC i funkcje globalne.  
  
 Tablica klasy pochodnym przypomina pochodnym listy.  
  
 Aby uzyskać więcej informacji o sposobie używania `CArray`, zapoznaj się z artykułem [kolekcji](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CArray`  
  
## <a name="requirements"></a>Wymagania  
 `Header:`afxtempl.h  
  
##  <a name="add"></a>CArray::Add  
 Dodaje nowy element do końca tablicy rośnie tablicy o 1.  
  
```  
INT_PTR Add(ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `ARG_TYPE`  
 Parametr szablonu określenie argumentów odwołania do elementów w tablicy tego typu.  
  
 `newElement`  
 Element, który ma zostać dodany do tej tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks elementu dodany.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli [SetSize](#setsize) został użyty z `nGrowBy` wartość większą niż 1, a następnie dodatkowa pamięć może zostać przydzielona. Jednak górna granica zwiększy się tylko 1.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#22](../../mfc/codesnippet/cpp/carray-class_1.cpp)]  
  
##  <a name="append"></a>CArray::Append  
 Wywołanie tej funkcji Członkowskich do dodania do końca innej zawartości tablicy.  
  
```  
INT_PTR Append(const CArray& src);
```  
  
### <a name="parameters"></a>Parametry  
 *src*  
 Źródło elementów do dołączenia do macierzy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks pierwszego elementu dołączany.  
  
### <a name="remarks"></a>Uwagi  
 Tablic muszą być tego samego typu.  
  
 W razie potrzeby **Append** mogą przydzielić dodatkową pamięć do uwzględnienia elementów dołączany do tablicy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#23](../../mfc/codesnippet/cpp/carray-class_2.cpp)]  
  
##  <a name="carray"></a>CArray::CArray  
 Tworzy pustą tablicę.  
  
```  
CArray();
```  
  
### <a name="remarks"></a>Uwagi  
 Tablica rozwoju jeden element naraz.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#24](../../mfc/codesnippet/cpp/carray-class_3.cpp)]  
  
##  <a name="copy"></a>CArray::Copy  
 Użyj tej funkcji członkowskich można kopiować elementy tablicy jednego do drugiego.  
  
```  
void Copy(const CArray& src);
```  
  
### <a name="parameters"></a>Parametry  
 *src*  
 Źródło elementów do skopiowania do tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich w celu zastąpienia elementów co tablica elementów innej tablicy.  
  
 **Kopia** nie spowoduje zwolnienia pamięci, ale w razie potrzeby **kopiowania** mogą przydzielić dodatkową pamięć do uwzględnienia elementów kopiowanych do tablicy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#25](../../mfc/codesnippet/cpp/carray-class_4.cpp)]  
  
##  <a name="elementat"></a>CArray::ElementAt  
 Zwraca tymczasowego odwołanie do określonego elementu w tablicy.  
  
```  
TYPE& ElementAt(INT_PTR nIndex);  
const TYPE& ElementAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez [GetUpperBound](#getupperbound).  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do elementu tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Służy do implementowania operator po lewej stronie przypisania dla tablic.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [GetSize](#getsize).  
  
##  <a name="freeextra"></a>CArray::FreeExtra  
 Zwalnia wszelkie dodatkowe pamięci przydzielony podczas tablicy został rozszerzony.  
  
```  
void FreeExtra();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja nie ma wpływu na rozmiar lub dolną granicę tablicy.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [GetData](#getdata).  
  
##  <a name="getat"></a>CArray::GetAt  
 Zwraca element tablicy w określonym indeksie.  
  
```  
TYPE& GetAt(INT_PTR nIndex);  
const TYPE& GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów tablicy.  
  
 `nIndex`  
 Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez [GetUpperBound](#getupperbound).  
  
### <a name="return-value"></a>Wartość zwracana  
 Element tablicy dla tego indeksu.  
  
### <a name="remarks"></a>Uwagi  
 Przekazywanie wartości ujemnej lub wartość większą niż wartość zwrócona przez `GetUpperBound` spowoduje potwierdzenia nie powiodło się.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#26](../../mfc/codesnippet/cpp/carray-class_5.cpp)]  
  
##  <a name="getcount"></a>CArray::GetCount  
 Zwraca liczbę elementów tablicy.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby pobrać liczbę elementów w tablicy. Ponieważ indeksy są liczony od zera, rozmiar jest większy niż największy indeks 1. Wywołanie tej metody spowoduje wygenerowanie takiego samego wyniku jako [CArray::GetSize](#getsize) metody.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#27](../../mfc/codesnippet/cpp/carray-class_6.cpp)]  
  
##  <a name="getdata"></a>CArray::GetData  
 Aby uzyskać bezpośredni dostęp do elementów w tablicy, należy użyć tej funkcji elementu członkowskiego.  
  
```  
const TYPE* GetData() const; 
TYPE* GetData();
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do elementu tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli elementy nie są dostępne, `GetData` zwraca wartość null.  
  
 Gdy bezpośredni dostęp do elementów tablicy pomoże szybciej, należy zachować ostrożność podczas wywoływania metody `GetData`; błędy wprowadzone bezpośrednio wpływa na elementy z tablicy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#28](../../mfc/codesnippet/cpp/carray-class_7.cpp)]  
  
##  <a name="getsize"></a>CArray::GetSize  
 Zwraca rozmiar tablicy.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ indeksy są liczony od zera, rozmiar jest większy niż największy indeks 1. Wywołanie tej metody spowoduje wygenerowanie takiego samego wyniku jako [CArray::GetCount](#getcount) metody.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#29](../../mfc/codesnippet/cpp/carray-class_8.cpp)]  
  
##  <a name="getupperbound"></a>CArray::GetUpperBound  
 Zwraca bieżący górna granica tej tablicy.  
  
```  
INT_PTR GetUpperBound() const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ indeksy tablicy są liczony od zera, funkcja zwraca wartość 1 mniej niż `GetSize`.  
  
 Warunek **(GetUpperBound)** = -1 oznacza, że tablica nie zawiera żadnych elementów.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CArray::GetAt](#getat).  
  
##  <a name="insertat"></a>CArray::InsertAt  
 Pierwszą wersję `InsertAt` wstawia jednego elementu (lub wiele kopii elementu) od określonego indeksu tablicy.  
  
```  
void InsertAt(
    INT_PTR nIndex,
    ARG_TYPE newElement,  
    INT_PTR nCount = 1);
 
void InsertAt(
    INT_PTR nStartIndex,  
    CArray* pNewArray);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczba całkowita indeksu, który może być większa niż wartość zwrócona przez `GetUpperBound`.  
  
 `ARG_TYPE`  
 Parametr szablonu określający typ elementów w tej macierzy.  
  
 `newElement`  
 Element ma być umieszczone w tej macierzy.  
  
 `nCount`  
 Ile razy ten element powinien być wstawiane (wartość domyślna to 1).  
  
 `nStartIndex`  
 Liczba całkowita indeksu, który może być większa niż wartość zwrócona przez [GetUpperBound](#getupperbound).  
  
 `pNewArray`  
 Innej tablicy, który zawiera elementy, które mają zostać dodane do tej tablicy.  
  
### <a name="remarks"></a>Uwagi  
 W procesie przewiduje (zwiększając wartość indeksu) istniejącego elementu tego indeksu, a przewiduje się wszystkie elementy powyżej.  
  
 Druga wersja wstawia wszystkie elementy z innego `CArray` kolekcji, zaczynając od `nStartIndex` pozycji.  
  
 `SetAt` Funkcji, natomiast zastępuje jeden element w określonej tablicy i nie przesunięcia żadnych elementów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#30](../../mfc/codesnippet/cpp/carray-class_9.cpp)]  
  
##  <a name="isempty"></a>CArray::IsEmpty  
 Określa, czy tablica jest pusta.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli macierz nie zawiera żadnych elementów; w przeciwnym razie 0.  
  
##  <a name="operator_at"></a>CArray::operator\[\]  
 Indeks dolny są to wygodny zastępuje [SetAt](#setat) i [GetAt](#getat) funkcji.  
  
```  
TYPE& operator[](int_ptr nindex);  
const TYPE& operator[](int_ptr nindex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów w tej macierzy.  
  
 `nIndex`  
 Indeks elementu można uzyskać dostęp.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy operator o nazwie dla tablic, które nie są **const**, mogą być używane w prawo (r) lub z lewej strony (wartości l) instrukcji przypisania. Druga Strona, wywoływana dla **const** tablic, mogą być używane tylko po prawej stronie.  
  
 Wersja do debugowania biblioteki potwierdza, jeśli indeks dolny (albo po lewej lub prawej stronie instrukcji przypisania) jest poza zakresem.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#34](../../mfc/codesnippet/cpp/carray-class_10.cpp)]  
  
##  <a name="relocateelements"></a>CArray::RelocateElements  
 Przenosi dane w buforze nowego podczas tablicy należy zwiększać i zmniejszać.  
  
```  
template<class TYPE, class ARG_TYPE>  
AFX_INLINE void CArray<TYPE, ARG_TYPE>::RelocateElements(
    TYPE* pNewData,  
    const TYPE* pData,  
    INT_PTR nCount);
```  
  
### <a name="parameters"></a>Parametry  
 `pNewData`  
 Bufor nowego tablicę elementów.  
  
 `pData`  
 Stary tablicę elementów.  
  
 `nCount`  
 Liczba elementów w tablicy stary.  
  
### <a name="remarks"></a>Uwagi  
 `pNewData`zawsze jest wystarczająco duży do przechowywania wszystkich `pData` elementów.  
  
 [Carray —](../../mfc/reference/carray-class.md) implementacja używa tej metody można skopiować do bufor nowego stare dane, gdy tablica należy zwiększać i zmniejszać (gdy [SetSize](#setsize) lub [FreeExtra](#freeextra) są nazywane). Domyślna implementacja tylko kopiuje dane.  
  
 Dla tablic, w którym element zawiera wskaźnik do jednego ze swoich własnych członków lub inną strukturę zawiera wskaźnik do jednego z elementów tablicy wskaźniki nie są aktualizowane w zwykłych kopii. W takim przypadku można rozwiązać wskaźniki zaimplementowanie specjalizacji `RelocateElements` z odpowiednich typów. Możesz również są odpowiedzialne za kopiowania danych.  
  
##  <a name="removeall"></a>CArray::RemoveAll  
 Usuwa wszystkie elementy z tej tablicy.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli tablica jest pusta, funkcja nadal działa.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#31](../../mfc/codesnippet/cpp/carray-class_11.cpp)]  
  
##  <a name="removeat"></a>CArray::RemoveAt  
 Usuwa jeden lub więcej elementów, zaczynając od określonego indeksu tablicy.  
  
```  
void RemoveAt(
    INT_PTR nIndex,  
    INT_PTR nCount = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez [GetUpperBound](#getupperbound).  
  
 `nCount`  
 Liczba elementów do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 W procesie klient przenosi dół wszystkie elementy powyżej usuniętych elementów. Go zmniejsza górna granica tablicy, ale nie spowoduje zwolnienia pamięci.  
  
 Próba usunięcia więcej elementów niż są zawarte w tablicy powyżej punktu usuwania wersja do debugowania biblioteki potwierdzeń.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#32](../../mfc/codesnippet/cpp/carray-class_12.cpp)]  
  
##  <a name="setat"></a>CArray::SetAt  
 Ustawia element tablicy w określonym indeksie.  
  
```  
void SetAt(INT_PTR nIndex, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez [GetUpperBound](#getupperbound).  
  
 `ARG_TYPE`  
 Parametr szablonu określenie typu argumenty używane dla odwołania do elementów tablicy.  
  
 `newElement`  
 Nowa wartość elementu mają być przechowywane w określonej pozycji.  
  
### <a name="remarks"></a>Uwagi  
 `SetAt`nie spowoduje tablicy się rozrastać. Użyj [SetAtGrow](#setatgrow) Jeśli chcesz tablicy, tak aby automatycznie powiększania.  
  
 Należy się upewnić, że wartość indeksu reprezentuje prawidłową pozycją w tablicy. Jeśli jest poza zakresem, wersja do debugowania biblioteki potwierdzeń.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [GetAt](#getat).  
  
##  <a name="setatgrow"></a>CArray::SetAtGrow  
 Ustawia element tablicy w określonym indeksie.  
  
```  
void SetAtGrow(INT_PTR nIndex, ARG_TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczba całkowita indeksu, który jest większa lub równa 0.  
  
 `ARG_TYPE`  
 Parametr szablonu określający typ elementów w tablicy.  
  
 `newElement`  
 Element, który ma zostać dodany do tej tablicy. A **NULL** wartość jest dozwolona.  
  
### <a name="remarks"></a>Uwagi  
 Tablica automatycznego zwiększania w razie potrzeby (górna granica jest dostosowane do uwzględnienia nowego elementu).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#33](../../mfc/codesnippet/cpp/carray-class_13.cpp)]  
  
##  <a name="setsize"></a>CArray::SetSize  
 Określa rozmiar pusta lub istniejącej tablicy; przydziela pamięć, jeśli to konieczne.  
  
```  
void SetSize(
    INT_PTR nNewSize,  
    INT_PTR nGrowBy = -1);
```  
  
### <a name="parameters"></a>Parametry  
 `nNewSize`  
 Nowy rozmiar tablicy (liczba elementów). Musi być większa lub równa 0.  
  
 `nGrowBy`  
 Minimalna liczba gniazd elementu można przydzielić, jeśli konieczne jest zwiększenie rozmiaru.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nowy rozmiar jest mniejszy niż stary rozmiar, zostanie obcięta tablicy i zwolnieniu wszystkich nieużywanej pamięci.  
  
 Użyj tej funkcji, aby ustawić rozmiar tablica, przed rozpoczęciem korzystania z tablicy. Jeśli nie używasz `SetSize`, dodawanie elementów do macierzy powoduje jego przydzielić często i skopiować. Częste zmiany alokacji i kopiowanie są mało wydajne i można fragmentu pamięci.  
  
 `nGrowBy` Parametr ma wpływ alokacji pamięci wewnętrznej podczas rośnie tablicy. Zgłoszone przez wykorzystanie przez niego nigdy nie wpływa na rozmiar tablicy [GetSize](#getsize) i [GetUpperBound](#getupperbound). Jeśli zostanie użyta domyślna wartość, MFC przydziela pamięci obliczane, aby uniknąć fragmentacji pamięci i zoptymalizować wydajność, w większości przypadków.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [GetData](#getdata).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC ZBIERANIE](../../visual-cpp-samples.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CObArray](../../mfc/reference/cobarray-class.md)   
 [Pomocnicy klasy kolekcji](../../mfc/reference/collection-class-helpers.md)
