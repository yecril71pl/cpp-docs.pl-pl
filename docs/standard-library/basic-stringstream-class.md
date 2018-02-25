---
title: "basic_stringstream — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
dev_langs:
- C++
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6616f5eadc5291b917d7121f5eebb92baeec8c3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="basicstringstream-class"></a>basic_stringstream — Klasa
Zawiera opis obiektu, który kontroluje wstawiania i wyodrębniania elementów i obiektów zakodowany przy użyciu buforu strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **elementu**, **Tr**, `Alloc`>.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>  
class basic_stringstream : public basic_iostream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parametry  
 `Alloc`  
 Klasa alokatora.  
  
 `Elem`  
 Typ podstawowy elementu ciągu.  
  
 *TR*  
 Specjalizowany cech znaków w elemencie podstawowe ciągu.  
  
## <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje obiekt, który kontroluje wstawiania i wyodrębniania elementów i obiektów zakodowany przy użyciu buforu strumienia klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **elementu**, **Tr**, `Alloc`>, elementami typu **elementu**, którego cech znaków są określane przez klasę **Tr**, a której elementy są przydzielane przez Program przydzielania klasy `Alloc`. Obiekt przechowuje obiekt basic_stringbuf — Klasa < **elementu**, **Tr**, `Alloc`>.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[basic_stringstream](#basic_stringstream)|Tworzy obiekt typu `basic_stringstream`.|  
  
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
  
##  <a name="allocator_type"></a>  basic_stringstream::allocator_type  
 Typ jest synonimem parametru szablonu `Alloc`.  
  
```  
typedef Alloc allocator_type;  
```  
  
##  <a name="basic_stringstream"></a>  basic_stringstream::basic_stringstream  
 Tworzy obiekt typu `basic_stringstream`.  
  
```  
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Mode`  
 Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `str`  
 Obiekt typu `basic_string`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje klasy podstawowej, przez wywołanie metody [basic_iostream —](../standard-library/basic-iostream-class.md)( **sb**), gdzie **sb** jest przechowywane obiekt klasy [basic_stringbuf —](../standard-library/basic-stringbuf-class.md) <  **Elementu**, **Tr**, `Alloc`>. Inicjuje również **sb** przez wywołanie basic_stringbuf — < **elementu**, **Tr**, `Alloc`> ( `_Mode`).  
  
 Drugi Konstruktor inicjuje klasy podstawowej, przez wywołanie basic_iostream — ( **sb**). Inicjuje również **sb** przez wywołanie basic_stringbuf — < **elementu**, **Tr**, `Alloc`> (_ *Str*, `_Mode`).  
  
##  <a name="rdbuf"></a>  basic_stringstream::rdbuf  
 Zwraca adres buforu strumienia przechowywanych typu **wskaźnika** do [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< **elementu**, **Tr**, `Alloc`>.  
  
```  
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Adres buforu strumienia przechowywanych typu **wskaźnika** do basic_stringbuf — < **elementu**, **Tr**, `Alloc`>.  
  
### <a name="example"></a>Przykład  
  Zobacz [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) na przykład, który używa `rdbuf`.  
  
##  <a name="str"></a>  basic_stringstream::str  
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

