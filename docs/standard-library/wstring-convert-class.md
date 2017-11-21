---
title: "wstring_convert — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- wstring/stdext::cvt::wstring_convert
- locale/std::wstring_convert::byte_string
- locale/std::wstring_convert::wide_string
- locale/std::wstring_convert::state_type
- locale/std::wstring_convert::int_type
- locale/std::wstring_convert::from_bytes
- locale/std::wstring_convert::to_bytes
- locale/std::wstring_convert::converted
- locale/std::wstring_convert::state
dev_langs: C++
helpviewer_keywords:
- stdext::cvt [C++], wstring_convert
- std::wstring_convert [C++], byte_string
- std::wstring_convert [C++], wide_string
- std::wstring_convert [C++], state_type
- std::wstring_convert [C++], int_type
- std::wstring_convert [C++], from_bytes
- std::wstring_convert [C++], to_bytes
- std::wstring_convert [C++], converted
- std::wstring_convert [C++], state
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e7a37fd636d376f379503d1dd1b95f05ac1828cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="wstringconvert-class"></a>wstring_convert — Klasa
Klasy szablonów `wstring_convert` wykonuje konwersje między ciąg typu wide i ciąg bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```  
  
#### <a name="parameters"></a>Parametry  
 Codecvt —  
 [Ustawień regionalnych](../standard-library/locale-class.md) aspektu reprezentujący obiekt konwersji.  
  
 Element  
 Typ elementu znaków dwubajtowych.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt, który kontroluje konwersje między obiektami ciągu typu wide klasy opisano klasy szablonu `std::basic_string<Elem>` i bajtów ciągu obiektów klasy `std::basic_string<char>` (znanej także jako `std::string`). Klasa szablonów Określa typy `wide_string` i `byte_string` jako synonimy dla tych dwóch typów. Konwersja między sekwencji `Elem` wartości (przechowywanych w `wide_string` obiektu) i wielobajtowych sekwencji (przechowywanej w `byte_string` obiektu) jest wykonywane przez obiekt klasy `Codecvt<Elem, char, std::mbstate_t>`, spełniający wymagania standardowego Konwersja kodu aspektu `std::codecvt<Elem, char, std::mbstate_t>`.  
  
 Przechowuje obiekt tej klasy szablonu:  
  
-   Ciąg do wyświetlania na błędy  
  
-   Ciąg typu wide do wyświetlania na błędy  
  
-   Wskaźnik do obiektu przydzielone konwersji (która jest zwolniony, gdy obiekt wbuffer_convert — zostanie zniszczony)  
  
-   Obiekt stanu konwersji typu [state_type](#state_type)  
  
-   Liczba konwersji  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[wstring_convert —](#wstring_convert)|Tworzy obiekt typu `wstring_convert`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[byte_string](#byte_string)|Typ, który reprezentuje ciąg bajtów.|  
|[wide_string](#wide_string)|Typ reprezentujący szeroki ciąg.|  
|[state_type](#state_type)|Typ, który reprezentuje stan konwersji.|  
|[int_type](#int_type)|Typ reprezentujący liczbę całkowitą.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[from_bytes](#from_bytes)|Konwertuje ciąg bajtów na ciąg typu wide.|  
|[to_bytes](#to_bytes)|Konwertuje ciąg typu wide ciąg bajtów.|  
|[konwertowane](#converted)|Zwraca liczbę konwersje powiodło się.|  
|[Stan](#state)|Zwraca obiekt reprezentujący stan konwersji.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
##  <a name="byte_string"></a>wstring_convert::byte_string  
 Typ, który reprezentuje ciąg bajtów.  
  
```
typedef std::basic_string<char> byte_string;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem `std::basic_string<char>`.  
  
##  <a name="converted"></a>wstring_convert::Converted  
 Zwraca liczbę konwersje powiodło się.  
  
```
size_t converted() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba pomyślnych konwersji.  
  
### <a name="remarks"></a>Uwagi  
 Liczba pomyślnych konwersji jest przechowywane w obiekcie Liczba konwersji.  
  
##  <a name="from_bytes"></a>wstring_convert::from_bytes  
 Konwertuje ciąg bajtów na ciąg typu wide.  
  
```
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Byte`|Sekwencja pojedynczego elementu bajtów do skonwertowania.|  
|`ptr`|C-style, zerem sekwencji znaków, które ma zostać przekonwertowany.|  
|`Bstr`|[Byte_string](#byte_string) do skonwertowania.|  
|`first`|Pierwszy znak w zakresie znaków ma zostać przekonwertowany.|  
|`last`|Ostatni znak w zakresie znaków ma zostać przekonwertowany.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt ciągu typu wide wynikającymi z konwersji.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli [stan konwersji](../standard-library/wstring-convert-class.md) obiekt był `not` skonstruowany przy jawną wartość, jest ustawiona na wartość domyślną (stan początkowy konwersji) przed rozpoczęciem konwersji. W przeciwnym razie jest pozostawiany bez zmian.  
  
 Liczba elementów wejściowych pomyślnie przekonwertowany jest przechowywane w obiekcie Liczba konwersji. Jeśli błąd konwersji nie wystąpi, funkcja członkowska zwraca skonwertowany szeroki ciąg. W przeciwnym razie jeśli obiekt został skonstruowany przy użyciu inicjatora komunikat o błędzie ciąg WWW, funkcji członkowskiej zwraca obiekt komunikat Błąd parametrów sieci. W przeciwnym razie funkcja członkowska zgłasza obiekt klasy [range_error —](../standard-library/range-error-class.md).  
  
##  <a name="int_type"></a>wstring_convert::int_type  
 Typ reprezentujący liczbę całkowitą.  
  
```
typedef typename wide_string::traits_type::int_type int_type;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem `wide_string::traits_type::int_type`.  
  
##  <a name="state"></a>wstring_convert::State  
 Zwraca obiekt reprezentujący stan konwersji.  
  
```
state_type state() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 [Stan konwersji](../standard-library/wstring-convert-class.md) obiekt, który reprezentuje stan konwersji.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="state_type"></a>wstring_convert::state_type  
 Typ, który reprezentuje stan konwersji.  
  
```
typedef typename Codecvt::state_type state_type;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ zawiera opis obiektu, który może reprezentować stan konwersji. Typ jest synonimem `Codecvt::state_type`.  
  
##  <a name="to_bytes"></a>wstring_convert::to_bytes  
 Konwertuje ciąg typu wide ciąg bajtów.  
  
```
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Char`|Znaków dwubajtowych, który ma zostać przekonwertowany.|  
|`Wptr`|C-style, zerem sekwencji, rozpoczynając od `wptr`, ma zostać przekonwertowany.|  
|`Wstr`|[Wide_string](#wide_string) do skonwertowania.|  
|`first`|Pierwszym elementem w zakresie elementów do skonwertowania.|  
|`last`|Ostatnim elementem w zakresie elementów do skonwertowania.|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli [stan konwersji](../standard-library/wstring-convert-class.md) obiekt był `not` skonstruowany przy jawną wartość, jest ustawiona na wartość domyślną (stan początkowy konwersji) przed rozpoczęciem konwersji. W przeciwnym razie jest pozostawiany bez zmian.  
  
 Liczba elementów wejściowych pomyślnie przekonwertowany jest przechowywane w obiekcie Liczba konwersji. Jeśli błąd konwersji nie wystąpi, funkcja członkowska zwraca ciąg przekonwertowany bajtów. W przeciwnym razie jeśli obiekt został skonstruowany przy użyciu inicjatora bajtów ciągu komunikat o błędzie, funkcji członkowskiej zwraca obiekt komunikat błędu bajtów ciągu. W przeciwnym razie funkcja członkowska zgłasza obiekt klasy [range_error —](../standard-library/range-error-class.md).  
  
##  <a name="wide_string"></a>wstring_convert::wide_string  
 Typ reprezentujący szeroki ciąg.  
  
```
typedef std::basic_string<Elem> wide_string;
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest synonimem `std::basic_string<Elem>`.  
  
##  <a name="wstring_convert"></a>wstring_convert::wstring_convert  
 Tworzy obiekt typu `wstring_convert`.  
  
```
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`*Pcvt`|Obiekt typu `Codecvt` do wykonania konwersji.|  
|`_State`|Obiekt typu [state_type](#state_type) reprezentujący stan konwersji.|  
|`_Berr`|[Byte_string](#byte_string) do wyświetlania na błędy.|  
|`Werr`|[Wide_string](#wide_string) do wyświetlania na błędy.|  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy magazynów konstruktora *Pcvt_arg* w [obiektu konwersji](../standard-library/wstring-convert-class.md)
