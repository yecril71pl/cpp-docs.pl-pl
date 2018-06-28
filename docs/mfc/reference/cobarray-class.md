---
title: Klasa CObArray | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
dev_langs:
- C++
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41165f177671379eecbc700df016cd19aea69962
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040210"
---
# <a name="cobarray-class"></a>Klasa CObArray
Obsługuje tablic `CObject` wskaźników.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CObArray : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CObArray::CObArray](#cobarray)|Konstruuje się pusta tablica `CObject` wskaźników.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CObArray::Add](#add)|Dodaje element do końca tablicy; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CObArray::Append](#append)|Dołącza innej tablicy do tablicy; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CObArray::Copy](#copy)|Kopiuje innej tablicy do tablicy; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CObArray::ElementAt](#elementat)|Zwraca tymczasowego odwołanie do wskaźnika elementu w tablicy.|  
|[CObArray::FreeExtra](#freeextra)|Zwalnia wszystkie nieużywanej pamięci powyżej bieżącego górną granicę.|  
|[CObArray::GetAt](#getat)|Zwraca wartość pod danym indeksem.|  
|[CObArray::GetCount](#getcount)|Pobiera liczbę elementów w tej macierzy.|  
|[CObArray::GetData](#getdata)|Umożliwia dostęp do elementów w tablicy. Może być **NULL**.|  
|[CObArray::GetSize](#getsize)|Pobiera liczbę elementów w tej macierzy.|  
|[CObArray::GetUpperBound](#getupperbound)|Zwraca największy nieprawidłowy indeks.|  
|[CObArray::InsertAt](#insertat)|Wstawia elementu (lub wszystkie elementy w innej tablicy) od określonego indeksu.|  
|[CObArray::IsEmpty](#isempty)|Określa, czy tablica jest pusta.|  
|[CObArray::RemoveAll](#removeall)|Usuwa wszystkie elementy z tej tablicy.|  
|[CObArray::RemoveAt](#removeat)|Usuwa element pod określonym indeksem.|  
|[CObArray::SetAt](#setat)|Ustawia wartość dla danego indeksu; Tablica nie może wzrosnąć.|  
|[CObArray::SetAtGrow](#setatgrow)|Ustawia wartość dla danego indeksu; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CObArray::SetSize](#setsize)|Ustawia liczbę elementów, które mają zostać zawarte w tej macierzy.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[[CObArray::operator]](#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|  
  
## <a name="remarks"></a>Uwagi  
 Tablice tych obiektów są podobne do tablic C, ale można dynamicznie zmniejszyć rozmiar i wzrostu w razie potrzeby.  
  
 Indeksy tablicy zawsze rozpoczynają się od pozycji 0. Można wybrać, czy rozwiązać górna granica, czy zezwalać tablicy, tak aby rozwinąć po dodaniu elementów poza bieżącą granicą. Jest przydzielana pamięć ciągłym górnej granicy, nawet jeśli niektóre elementy mają wartość null.  
  
 W obszarze Win32, rozmiar `CObArray` obiektu jest ograniczony tylko do dostępnej pamięci.  
  
 Za pomocą tablicy C, czas dostępu dla `CObArray` indeksowanego elementu jest stała i nie zależy od rozmiaru tablicy.  
  
 `CObArray` zawiera implement_serial — makro do obsługi serializacji i zrzucanie swoich elementów. Jeśli tablica `CObject` wskaźniki są przechowywane do archiwum z operatorem przeciążone wstawiania lub z `Serialize` wszystkich funkcji członkowskiej `CObject` element z kolei serializacji wraz z jego indeksu tablicy.  
  
 Jeśli potrzebujesz zrzutu osoba `CObject` elementów w tablicy, należy ustawić głębokość `CDumpContext` obiekt do 1 lub większą.  
  
 Gdy `CObArray` obiekt jest usunięty lub gdy jego elementy są usuwane, tylko `CObject` wskaźniki są usuwane i nie obiektów odwołujących się.  
  
> [!NOTE]
>  Przed rozpoczęciem korzystania z tablicy, użyj `SetSize` jego rozmiar i przydzielić pamięci dla niego. Jeśli nie używasz `SetSize`, dodawanie elementów do macierzy powoduje jego przydzielić często i skopiować. Częste zmiany alokacji i kopiowanie są mało wydajne i można fragmentu pamięci.  
  
 Tablica pochodnym klasy jest podobna do wyprowadzenia listy. Aby uzyskać szczegółowe informacje na pochodnym klasy listy specjalnych, zobacz artykuł [kolekcji](../../mfc/collections.md).  
  
> [!NOTE]
>  Implement_serial — makro należy użyć w implementacji klasy pochodnej, jeśli zamierzasz serializować tablicy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObArray`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcoll.h  
  
##  <a name="add"></a>  CObArray::Add  
 Dodaje nowy element do końca tablicy rośnie tablicy o 1.  
  
```  
INT_PTR Add(CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *newElement*  
 `CObject` Wskaźnika do dodania do tej tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks elementu dodany.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli [SetSize](#setsize) został użyty z *nGrowBy* wartość większą niż 1, a następnie dodatkowa pamięć może zostać przydzielona. Jednak górna granica zwiększy się tylko 1.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::Add`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Dodaj INT_PTR (BYTE** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Dodaj INT_PTR (DWORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Dodaj INT_PTR (void\***  `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Dodaj INT_PTR (LPCTSTR** `newElement` **); throw (CMemoryException\* );**<br /><br /> **INT_PTR Add(const CString&** `newElement` **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Dodaj INT_PTR (UINT** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Dodaj INT_PTR (WORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `Add example: A CObArray with 2 elements`  
  
 `[0] = a CAge at $442A 21`  
  
 `[1] = a CAge at $4468 40`  
  
##  <a name="append"></a>  CObArray::Append  
 Wywołanie tej funkcji Członkowskich, aby dodać zawartość innej tablicy na końcu podanej tablicy.  
  
```  
INT_PTR Append(const CObArray& src);
```  
  
### <a name="parameters"></a>Parametry  
 *src*  
 Źródło elementów do dołączenia do macierzy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks pierwszego elementu dołączany.  
  
### <a name="remarks"></a>Uwagi  
 Tablic muszą być tego samego typu.  
  
 W razie potrzeby `Append` mogą przydzielić dodatkową pamięć do uwzględnienia elementów dołączany do tablicy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::Append`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Dołącz INT_PTR (const CByteArray &** *src* **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Dołącz INT_PTR (const CDWordArray &** *src* **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Dołącz INT_PTR (const CPtrArray &** *src* **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Dołącz INT_PTR (const CStringArray &** *src* **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Dołącz INT_PTR (const CUIntArray &** *src* **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Dołącz INT_PTR (const CWordArray &** *src* **);**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]  
  
##  <a name="copy"></a>  CObArray::Copy  
 Wywołanie tej funkcji Członkowskich w celu zastąpienia elementy danej tablicy elementów tablicy innego tego samego typu.  
  
```  
void Copy(const CObArray& src);
```  
  
### <a name="parameters"></a>Parametry  
 *src*  
 Źródło elementów do skopiowania do tablicy.  
  
### <a name="remarks"></a>Uwagi  
 `Copy` nie spowoduje zwolnienia pamięci. Jednakże, jeśli to konieczne, `Copy` mogą przydzielić dodatkową pamięć do uwzględnienia elementów kopiowanych do tablicy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::Copy`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Unieważnij kopiowania (const CByteArray &** *src* **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Unieważnij kopiowania (const CDWordArray &** *src* **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Unieważnij kopiowania (const CPtrArray &** *src* **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Unieważnij kopiowania (const CStringArray &** *src* **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Unieważnij kopiowania (const CUIntArray &** *src* **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Unieważnij kopiowania (const CWordArray &** *src* **);**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]  
  
##  <a name="cobarray"></a>  CObArray::CObArray  
 Tworzy pustą `CObject` wskaźnika tablicy.  
  
```  
CObArray();
```  
  
### <a name="remarks"></a>Uwagi  
 Tablica rozwoju jeden element naraz.  
  
 W poniższej tabeli przedstawiono inne konstruktorów, które są podobne do `CObArray::CObArray`.  
  
|Class|Konstruktor|  
|-----------|-----------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray ();**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray ();**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray ();**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray ();**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray ();**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray ();**|  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]  
  
##  <a name="elementat"></a>  CObArray::ElementAt  
 Zwraca tymczasowego odwołanie do wskaźnika elementu w tablicy.  
  
```  
CObject*& ElementAt(INT_PTR nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez `GetUpperBound`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do `CObject` wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Służy do implementowania operator po lewej stronie przypisania dla tablic. Należy pamiętać, że to zaawansowanych funkcji, które mają być używane tylko w celu wykonania operatory specjalne tablicy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::ElementAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BAJT & ElementAt (INT_PTR** `nIndex` **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & ElementAt (INT_PTR** `nIndex` **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& ElementAt (INT_PTR** `nIndex` **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Cstring — & ElementAt (INT_PTR** `nIndex` **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & ElementAt (INT_PTR** `nIndex` **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD & ElementAt (INT_PTR** `nIndex` **);**|  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CObArray::GetSize](#getsize).  
  
##  <a name="freeextra"></a>  CObArray::FreeExtra  
 Zwalnia wszelkie dodatkowe pamięci przydzielony podczas tablicy został rozszerzony.  
  
```  
void FreeExtra();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja nie ma wpływu na rozmiar lub dolną granicę tablicy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::FreeExtra`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra ();**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra ();**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra ();**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra ();**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra ();**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra ();**|  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CObArray::GetData](#getdata).  
  
##  <a name="getat"></a>  CObArray::GetAt  
 Zwraca element tablicy w określonym indeksie.  
  
```  
CObject* GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez `GetUpperBound`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `CObject` Wskaźnika element dla tego indeksu.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Przekazywanie wartości ujemnej lub wartość większą niż wartość zwrócona przez `GetUpperBound` spowoduje potwierdzenia nie powiodło się.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::GetAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**GetAt BAJTÓW (INT_PTR** `nIndex` **) const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt (INT_PTR** `nIndex` **) const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt (INT_PTR** `nIndex` **) const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Cstring — GetAt (INT_PTR** `nIndex` **) const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt (INT_PTR** `nIndex` **) const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt (INT_PTR** `nIndex` **) const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]  
  
##  <a name="getcount"></a>  CObArray::GetCount  
 Zwraca liczbę elementów tablicy.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby pobrać liczbę elementów w tablicy. Ponieważ indeksy są liczony od zera, rozmiar jest większy niż największy indeks 1.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::GetCount`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount () const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount () const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount () const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount () const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount () const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]  
  
##  <a name="getdata"></a>  CObArray::GetData  
 Aby uzyskać bezpośredni dostęp do elementów w tablicy, należy użyć tej funkcji elementu członkowskiego.  
  
```  
const CObject** GetData() const;  
  
CObject** GetData();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do tablicy `CObject` wskaźników.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli elementy nie są dostępne, `GetData` zwraca wartość null.  
  
 Gdy bezpośredni dostęp do elementów tablicy pomoże szybciej, należy zachować ostrożność podczas wywoływania metody `GetData`; błędy wprowadzone bezpośrednio wpływa na elementy z tablicy.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::GetData`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Const BAJTÓW\* () GetData const; BAJT\* GetData ();**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Const DWORD\* GetData const (); DWORD\* GetData ();**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Const void\* \* (GetData) const; void\* \* GetData ();**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**cstring — stała\* () GetData const; Cstring —\* GetData ();**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Const UINT\* () GetData const; UINT\* GetData ();**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Const WORD\* () GetData const; WORD\* GetData ();**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]  
  
##  <a name="getsize"></a>  CObArray::GetSize  
 Zwraca rozmiar tablicy.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ indeksy są liczony od zera, rozmiar jest większy niż największy indeks 1.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::GetSize`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetSize () const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetSize () const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetSize () const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetSize () const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetSize () const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetSize () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]  
  
##  <a name="getupperbound"></a>  CObArray::GetUpperBound  
 Zwraca bieżący górna granica tej tablicy.  
  
```  
INT_PTR GetUpperBound() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks (liczony od zera) górnej granicy.  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ indeksy tablicy są liczony od zera, funkcja zwraca wartość 1 mniej niż `GetSize`.  
  
 Warunek **(GetUpperBound)** = -1 oznacza, że tablica nie zawiera żadnych elementów.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::GetUpperBound`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound () const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound () const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound () const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound () const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound () const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound () const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]  
  
##  <a name="insertat"></a>  CObArray::InsertAt  
 Wstawia elementu (lub wszystkie elementy w innej tablicy) od określonego indeksu.  
  
```  
void InsertAt(
    INT_PTR nIndex,  
    CObject* newElement,  
    INT_PTR nCount = 1);

 
void InsertAt(
    INT_PTR nStartIndex,  
    CObArray* pNewArray);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczba całkowita indeksu, który może być większa niż wartość zwrócona przez `GetUpperBound`.  
  
 *newElement*  
 `CObject` Wskaźnika, które mają być umieszczone w tej macierzy. A *newElement* wartości **NULL** jest dozwolone.  
  
 *nCount*  
 Ile razy ten element powinien być wstawiane (wartość domyślna to 1).  
  
 *nStartIndex*  
 Liczba całkowita indeksu, który może być większa niż wartość zwrócona przez `GetUpperBound`.  
  
 *pNewArray*  
 Innej tablicy, który zawiera elementy, które mają zostać dodane do tej tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszą wersję `InsertAt` wstawia jednego elementu (lub wiele kopii elementu) od określonego indeksu tablicy. W procesie przewiduje (zwiększając wartość indeksu) istniejącego elementu tego indeksu, a przewiduje się wszystkie elementy powyżej.  
  
 Druga wersja wstawia wszystkie elementy z innego `CObArray` kolekcji, zaczynając od *nStartIndex* pozycji.  
  
 `SetAt` Funkcji, natomiast zastępuje jeden element w określonej tablicy i nie przesunięcia żadnych elementów.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::InsertAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, BYTE** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CByteArray\***  `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CDWordArray\***  `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, void\***  `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CPtrArray\***  `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CStringArray\***  `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, UINT** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CUIntArray\***  `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, WORD** `newElement` **, int** `nCount` **= 1);**<br /><br /> **throw (CMemoryException\* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CWordArray\***  `pNewArray` **);**<br /><br /> **throw (CMemoryException\* );**|  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `InsertAt example: A CObArray with 3 elements`  
  
 `[0] = a CAge at $45C8 21`  
  
 `[1] = a CAge at $4646 30`  
  
 `[2] = a CAge at $4606 40`  
  
##  <a name="isempty"></a>  CObArray::IsEmpty  
 Określa, czy tablica jest pusta.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli tablica jest pusta. w przeciwnym razie 0.  
  
##  <a name="operator_at"></a>  [CObArray::operator]  
 Indeks dolny są to wygodny zastępuje `SetAt` i `GetAt` funkcji.  
  
```  
CObject*& operator[](int_ptr nindex);  
CObject* operator[](int_ptr nindex) const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy operator o nazwie dla tablic, które nie są **const**, mogą być używane w prawo (r) lub z lewej strony (wartości l) instrukcji przypisania. Druga Strona, wywoływana dla **const** tablic, mogą być używane tylko po prawej stronie.  
  
 Wersja do debugowania biblioteki potwierdza, jeśli indeks dolny (albo po lewej lub prawej stronie instrukcji przypisania) jest poza zakresem.  
  
 W poniższej tabeli przedstawiono inne operatory, które są podobne do **[CObArray::operator]**.  
  
|Class|Operator|  
|-----------|--------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BAJT & — operator [] (int_ptr** `nindex`  **\);**<br /><br /> **BYTE [] — operator (int_ptr** `nindex`  **\) const;**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD & — operator [] (int_ptr** `nindex`  **\);**<br /><br /> **DWORD operatora [] (int_ptr** `nindex`  **\) const;**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& — operator [] (int_ptr** `nindex`  **\);**<br /><br /> **void\* operatora [] (int_ptr** `nindex`  **\) const;**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Cstring — & — operator [] (int_ptr** `nindex`  **\);**<br /><br /> **Cstring — operator [] (int_ptr** `nindex`  **\) const;**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT & — operator [] (int_ptr** `nindex`  **\);**<br /><br /> **UINT operatora [] (int_ptr** `nindex`  **\) const;**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD & — operator [] (int_ptr** `nindex`  **\);**<br /><br /> **WORD operatora [] (int_ptr** `nindex`  **\) const;**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]  
  
##  <a name="removeall"></a>  CObArray::RemoveAll  
 Usuwa wszystkie wskaźniki z tej tablicy, ale nie powoduje usunięcia faktycznie `CObject` obiektów.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli tablica jest pusta, funkcja nadal działa.  
  
 `RemoveAll` Funkcja zwalnia wszystkie pamięć używana na potrzeby magazynu wskaźnika.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::RemoveAll`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll( );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll( );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll( );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll( );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll( );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll( );**|  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]  
  
##  <a name="removeat"></a>  CObArray::RemoveAt  
 Usuwa jeden lub więcej elementów, zaczynając od określonego indeksu tablicy.  
  
```  
void RemoveAt(
    INT_PTR nIndex,  
    INT_PTR nCount = 1);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez `GetUpperBound`.  
  
 *nCount*  
 Liczba elementów do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 W procesie klient przenosi dół wszystkie elementy powyżej usuniętych elementów. Go zmniejsza górna granica tablicy, ale nie spowoduje zwolnienia pamięci.  
  
 Próba usunięcia więcej elementów niż są zawarte w tablicy powyżej punktu usuwania wersja do debugowania biblioteki potwierdzeń.  
  
 `RemoveAt` Funkcji usuwa `CObject` wskaźnika z tablicy, ale nie powoduje usunięcia danego obiektu.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::RemoveAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Element RemoveAt void (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Element RemoveAt void (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Element RemoveAt void (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Element RemoveAt void (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Element RemoveAt void (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Element RemoveAt void (INT_PTR** `nIndex` **, INT_PTR** *nCount* **= 1);**|  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `RemoveAt example: A CObArray with 1 elements`  
  
 `[0] = a CAge at $4606 40`  
  
##  <a name="setat"></a>  CObArray::SetAt  
 Ustawia element tablicy w określonym indeksie.  
  
```  
void SetAt(
    INT_PTR nIndex,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez `GetUpperBound`.  
  
 *newElement*  
 Wskaźnik obiektu ma zostać wstawiony w tej macierzy. A **NULL** wartość jest dozwolona.  
  
### <a name="remarks"></a>Uwagi  
 `SetAt` nie spowoduje tablicy się rozrastać. Użyj `SetAtGrow` Jeśli chcesz tablicy, tak aby automatycznie powiększania.  
  
 Należy się upewnić, że wartość indeksu reprezentuje prawidłową pozycją w tablicy. Jeśli jest poza zakresem, wersja do debugowania biblioteki potwierdzeń.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::SetAt`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt (INT_PTR** `nIndex` **, BYTE** `newElement` **);**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, DWORD** `newElement` **);**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, void\***  `newElement` **);**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, UINT** `newElement` **);**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, WORD** `newElement` **);**|  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `SetAt example: A CObArray with 2 elements`  
  
 `[0] = a CAge at $47E0 30`  
  
 `[1] = a CAge at $47A0 40`  
  
##  <a name="setatgrow"></a>  CObArray::SetAtGrow  
 Ustawia element tablicy w określonym indeksie.  
  
```  
void SetAtGrow(
    INT_PTR nIndex,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczba całkowita indeksu, który jest większa lub równa 0.  
  
 *newElement*  
 Wskaźnik obiektu ma zostać dodany do tej tablicy. A **NULL** wartość jest dozwolona.  
  
### <a name="remarks"></a>Uwagi  
 Tablica automatycznego zwiększania w razie potrzeby (górna granica jest dostosowane do uwzględnienia nowego elementu).  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::SetAtGrow`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, BYTE** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, DWORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, void\***  `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, UINT** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, WORD** `newElement` **);**<br /><br /> **throw (CMemoryException\* );**|  
  
### <a name="example"></a>Przykład  
  Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w wszystkie przykłady w kolekcji.  
  
 [!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]  
  
 Wyniki z tego programu są następujące:  
  
 `SetAtGrow example: A CObArray with 4 elements`  
  
 `[0] = a CAge at $47C0 21`  
  
 `[1] = a CAge at $4800 40`  
  
 `[2] = NULL`  
  
 `[3] = a CAge at $4840 65`  
  
##  <a name="setsize"></a>  CObArray::SetSize  
 Określa rozmiar pusta lub istniejącej tablicy; przydziela pamięć, jeśli to konieczne.  
  
```  
void SetSize(
    INT_PTR nNewSize,  
    INT_PTR nGrowBy = -1);
```  
  
### <a name="parameters"></a>Parametry  
 *nNewSize*  
 Nowy rozmiar tablicy (liczba elementów). Musi być większa lub równa 0.  
  
 *nGrowBy*  
 Minimalna liczba gniazd elementu można przydzielić, jeśli konieczne jest zwiększenie rozmiaru.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli nowy rozmiar jest mniejszy niż stary rozmiar, zostanie obcięta tablicy i zwolnieniu wszystkich nieużywanej pamięci. W celu zwiększenia wydajności, należy wywołać `SetSize` można ustawić rozmiar tablicy przed jego użyciem. Zapobiega to potrzebę Przydziel ponownie, a następnie skopiuj tablicy za każdym razem, gdy element zostanie dodany.  
  
 *NGrowBy* parametr ma wpływ alokacji pamięci wewnętrznej podczas rośnie tablicy. Zgłoszone przez wykorzystanie przez niego nigdy nie wpływa na rozmiar tablicy `GetSize` i `GetUpperBound`.  
  
 Jeśli rozmiar tablicy został rozszerzony, wszystkie nowo przydzielone **CObject \***  wskaźniki jest ustawiana wartość NULL.  
  
 W poniższej tabeli przedstawiono innego członka funkcje, które są podobne do `CObArray::SetSize`.  
  
|Class|Funkcja elementów członkowskich|  
|-----------|---------------------|  
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|  
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|  
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|  
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|  
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|  
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize (INT_PTR** `nNewSize` **, int** `nGrowBy` **= -1);**<br /><br /> **throw (CMemoryException\* );**|  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CObArray::GetData](#getdata).  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CStringArray](../../mfc/reference/cstringarray-class.md)   
 [Klasa CPtrArray](../../mfc/reference/cptrarray-class.md)   
 [Klasa CByteArray](../../mfc/reference/cbytearray-class.md)   
 [Klasa CWordArray](../../mfc/reference/cwordarray-class.md)   
 [Klasa CDWordArray](../../mfc/reference/cdwordarray-class.md)
