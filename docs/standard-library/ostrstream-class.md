---
title: "ostrstream — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
dev_langs: C++
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 42b0786a140cf9657257d7f79a225a0473115282
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ostrstream-class"></a>ostrstream — Klasa
Opis obiektu, który kontroluje wstawiania elementów i obiektów zakodowanych do buforu strumienia klasy [strstreambuf —](../standard-library/strstreambuf-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```
class ostrstream : public ostream
```  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przechowuje obiekt klasy `strstreambuf`.  
  
> [!NOTE]
>  Ta klasa jest przestarzały. Należy rozważyć użycie [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) lub [wostringstream](../standard-library/sstream-typedefs.md#wostringstream) zamiast tego.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[ostrstream —](#ostrstream)|Tworzy obiekt typu `ostrstream`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[blokowanie](#freeze)|Powoduje, że jest niedostępna za pośrednictwem operacji buforu strumienia buforu strumienia.|  
|[pcount](#pcount)|Zwraca liczbę z liczbą elementów zapisywane w kontrolowanej sekwencji.|  
|[rdbuf](#rdbuf)|Zwraca wskaźnik do strumienia powiązanych `strstreambuf` obiektu.|  
|[str](#str)|Wywołania [Zablokuj](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<strstream — >  
  
 **Namespace:** Standard  
  
##  <a name="freeze"></a>ostrstream::FREEZE  
 Powoduje, że jest niedostępna za pośrednictwem operacji buforu strumienia buforu strumienia.  
  
```
void freeze(bool _Freezeit = true);
```  
  
### <a name="parameters"></a>Parametry  
 `_Freezeit`  
 A `bool` wskazującą, czy ma strumień jest zablokowana.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji Członkowskich [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).  
  
### <a name="example"></a>Przykład  
  Zobacz [strstream::freeze](../standard-library/strstreambuf-class.md#freeze) na przykład, który używa **Zablokuj**.  
  
##  <a name="ostrstream"></a>ostrstream::ostrstream  
 Tworzy obiekt typu `ostrstream`.  
  
```
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Bufor.  
  
 `count`  
 Rozmiar buforu w bajtach.  
  
 `_Mode`  
 Tryb wejściowymi i wyjściowymi buforu. Zobacz [ios_base::openmode](../standard-library/ios-base-class.md#openmode) Aby uzyskać więcej informacji.  
  
### <a name="remarks"></a>Uwagi  
 Oba konstruktory zainicjowanie klasy głównej przez wywołanie metody [ostream](../standard-library/ostream-typedefs.md#ostream)( **sb**), gdzie **sb** jest przechowywane obiekt klasy [strstreambuf —](../standard-library/strstreambuf-class.md). Pierwszy Konstruktor inicjuje również **sb** przez wywołanie metody `strstreambuf`. Drugi Konstruktor inicjuje klasy podstawowej, jeden z dwóch sposobów:  
  
-   Jeśli `_Mode`  &  **ios_base::app**== 0, następnie `ptr` musi wyznaczyć pierwszy element tablicy `count` elementów i wywołania konstruktora `strstreambuf`( `ptr`, `count`, `ptr`).  
  
-   W przeciwnym razie `ptr` musi wyznaczyć pierwszy element tablicy liczba elementów zawierający parametry C których pierwszy element określony przez `ptr`i wywołania konstruktora `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) ).  
  
##  <a name="pcount"></a>ostrstream::pcount  
 Zwraca liczbę z liczbą elementów zapisywane w kontrolowanej sekwencji.  
  
```
streamsize pcount() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów zapisywane w kontrolowanej sekwencji.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).  
  
### <a name="example"></a>Przykład  
  Zobacz [strstream::pcount](../standard-library/strstreambuf-class.md#pcount) dla przykładu korzystającego z `pcount`.  
  
##  <a name="rdbuf"></a>ostrstream::rdbuf  
 Zwraca wskaźnik do obiektu skojarzone strstreambuf — strumienia.  
  
```
strstreambuf *rdbuf() const
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do strumienia powiązanych strstreambuf — obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca adres buforu strumienia przechowywanych typu **wskaźnika** do [strstreambuf —](../standard-library/strstreambuf-class.md).  
  
### <a name="example"></a>Przykład  
  Zobacz [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) dla przykładu korzystającego z `rdbuf`.  
  
##  <a name="str"></a>ostrstream::str  
 Wywołania [Zablokuj](../standard-library/strstreambuf-class.md#freeze), a następnie zwraca wskaźnik do początku kontrolowanej sekwencji.  
  
```
char *str();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do początku kontrolowanej sekwencji.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).  
  
### <a name="example"></a>Przykład  
  Zobacz [strstream::str](../standard-library/strstreambuf-class.md#str) dla przykładu korzystającego z **str**.  
  
## <a name="see-also"></a>Zobacz też  
 [ostream](../standard-library/ostream-typedefs.md#ostream)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)



