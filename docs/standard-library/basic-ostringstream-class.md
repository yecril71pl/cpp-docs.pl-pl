---
title: "basic_ostringstream — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
dev_langs: C++
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4a5d494d28872bf5e59f0c436ceb037bd36a94c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="basicostringstream-class"></a>basic_ostringstream — Klasa
Opis obiektu, który kontroluje wstawiania elementów i obiektów zakodowanych do buforu strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **elementu**, **Tr**, `Alloc`>.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>  
class basic_ostringstream : public basic_ostream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parametry  
 `Alloc`  
 Klasa alokatora.  
  
 `Elem`  
 Typ podstawowy elementu ciągu.  
  
 *TR*  
 Specjalizowany cech znaków w elemencie podstawowe ciągu.  
  
## <a name="remarks"></a>Uwagi  
 Klasa opisuje obiekt, który kontroluje wstawiania elementów i obiektów zakodowanych w buforze strumienia, elementami typu **elementu**, którego cech znaków są określane przez klasę **Tr**i których elementy są przydzielane przez program przydzielania klasy `Alloc`. Obiekt przechowuje obiekt basic_stringbuf — Klasa < **elementu**, **Tr**, `Alloc`>.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[basic_ostringstream —](#basic_ostringstream)|Tworzy obiekt typu `basic_ostringstream`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Typ jest synonimem parametru szablonu `Alloc`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[rdbuf](#rdbuf)|Zwraca adres buforu strumienia przechowywanych typu `pointer` do [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|  
|[str](#str)|Ustawia lub pobiera tekst w buforze ciągu bez zmiany pozycji zapisu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<sstream — >  
  
 **Namespace:** Standard  
  
##  <a name="allocator_type"></a>basic_ostringstream::allocator_type  
 Typ jest synonimem parametru szablonu `Alloc`.  
  
```  
typedef Alloc allocator_type;  
```  
  
##  <a name="basic_ostringstream"></a>basic_ostringstream::basic_ostringstream  
 Tworzy obiekt basic_ostringstream — typu.  
  
```  
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Mode`  
 Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `str`  
 Obiekt typu `basic_string`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje klasy podstawowej, przez wywołanie metody [basic_ostream —](../standard-library/basic-ostream-class.md)( **sb**), gdzie **sb** jest przechowywane obiekt klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md) <  **Elementu**, **Tr**, `Alloc`>. Inicjuje również **sb** przez wywołanie basic_stringbuf — < **elementu**, **Tr**, `Alloc`> ( `_Mode` &#124; `ios_base::out`).  
  
 Drugi Konstruktor inicjuje klasy podstawowej, przez wywołanie basic_ostream — ( **sb**). Inicjuje również **sb** przez wywołanie basic_stringbuf — < **elementu**, **Tr**, `Alloc`> (_ *Str*, `_Mode` &#124; `ios_base::out`).  
  
##  <a name="rdbuf"></a>basic_ostringstream::rdbuf  
 Zwraca adres buforu strumienia przechowywanych typu **wskaźnika** do [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **elementu**, **Tr**, `Alloc`>.  
  
```  
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Adres buforu przechowywanych strumienia, typu **wskaźnika** do basic_stringbuf — < **elementu**, **Tr**, `Alloc`>.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca adres buforu strumienia przechowywanych typu **wskaźnika** do basic_stringbuf — < **elementu**, **Tr**, `Alloc`>.  
  
### <a name="example"></a>Przykład  
  Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który używa `rdbuf`.  
  
##  <a name="str"></a>basic_ostringstream::str  
 Ustawia lub pobiera tekst w buforze ciągu bez zmiany pozycji zapisu.  
  
```  
basic_string<Elem, Tr, Alloc> str() const;

 
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```  
  
### <a name="parameters"></a>Parametry  
 `_Newstr`  
 Nowe parametry.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca obiekt klasy [basic_string —](../standard-library/basic-string-class.md)< **elementu**, **Tr**, `Alloc`>, którego kopię sekwencji kontrolowane przez jest kontrolowanej sekwencji  **\*to**.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca pierwszy funkcji członkowskiej [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Drugi wywołania funkcji Członkowskich `rdbuf`  ->  **str**( `_Newstr`).  
  
### <a name="example"></a>Przykład  
  Zobacz [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) na przykład, który używa **str**.  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)

