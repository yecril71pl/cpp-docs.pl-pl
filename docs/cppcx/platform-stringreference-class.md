---
title: Klasa platform::StringReference | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::StringReference::StringReference
- VCCORLIB/Platform::StringReference::Data
- VCCORLIB/Platform::StringReference::Length
- VCCORLIB/Platform::StringReference::GetHSTRING
- VCCORLIB/Platform::StringReference::GetString
dev_langs: C++
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: bf096ef9849856e9995ff634d7aca26cd7f3f8e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="platformstringreference-class"></a>Klasa platform::StringReference
Typem optymalizacji, który służy do przekazywania danych ciąg z `Platform::String^` parametrów do innych metod z co najmniej operacje kopiowania wejściowych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
class StringReference  
```  
  
### <a name="remarks"></a>Uwagi  
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[StringReference::StringReference](#ctor)|Dwa konstruktory do tworzenia wystąpień `StringReference`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[StringReference::Data](#data)|Zwraca ciąg danych jako tablica wartości char16.|  
|[StringReference::Length](#length)|Zwraca liczbę znaków w ciągu.|  
|[StringReference::GetHSTRING](#gethstring)|Zwraca dane ciąg jako wartość HSTRING.|  
|[StringReference::GetString](#getstring)|Zwraca ciąg dane jako `Platform::String^`.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[StringReference::operator =](#operator-assign)|Przypisuje `StringReference` na nowy `StringReference` wystąpienia.|  
|[StringReference::operator()](#operator-call)|Konwertuje `StringReference` do `Platform::String^`.|  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Nagłówek:** vccorlib.h  

## <a name="data"></a>StringReference::Data — metoda
Zwraca zawartość to `StringReference` jako tablica wartości char16.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
const ::default::char16 * Data() const  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Tablica znaków tekst UNICODE char16.  
  


## <a name="gethstring"></a>StringReference::GetHSTRING — metoda
Zwraca zawartość jako ciąg `__abi_HSTRING`.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
__abi_HSTRING GetHSTRING() const  
  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `__abi_HSTRING` Zawierający danych ciągu.  
  
### <a name="remarks"></a>Uwagi  
  


## <a name="getstring"></a>StringReference::GetString — metoda
Zwraca zawartość jako ciąg `Platform::String^`.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
__declspec(no_release_return) __declspec(no_refcount)  
    ::Platform::String^ GetString() const  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `Platform::String^` zawierający danych ciągu.  

## <a name="length"></a>StringReference::Length — metoda
Zwraca liczbę znaków w ciągu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
unsigned int Length() const  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba całkowita bez znaku, która określa liczbę znaków w ciągu.  
  
### <a name="remarks"></a>Uwagi  
  


## <a name="operator-assign"></a>StringReference::operator = — Operator
Przypisuje określony obiekt do bieżącego `StringReference` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
StringReference& operator=(const StringReference& __fstrArg);  
StringReference& operator=(const ::default::char16* __strArg);    
```  
  
### <a name="parameters"></a>Parametry  
 `__fstrArg`  
 Adres `StringReference` obiekt, który służy do inicjowania bieżącego `StringReference` obiektu.  
  
 `__strArg`  
 Wskaźnik do tablicy wartości char16 służy do inicjowania bieżącego `StringReference` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu typu `StringReference`.  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ `StringReference` jest klasą standard C++ i nie klasy referencyjnej, nie ma w **przeglądarki obiektów**.  
  


## <a name="operator-call"></a>StringReference::operator() Operator
Konwertuje `StringReference` do obiektu `Platform::String^` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
__declspec(no_release_return) __declspec(no_refcount)  
         operator ::Platform::String^() const  
  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do typu obiektu `Platform::String`.  

## <a name="ctor"></a>Konstruktor StringReference::StringReference
Inicjuje nowe wystąpienie klasy `StringReference` klasy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
    StringReference();  
  
   StringReference(const StringReference& __fstrArg)  
  
StringReference(const ::default::char16* __strArg)  
  
StringReference(const ::default::char16* __strArg, size_t __lenArg)  
```  
  
### <a name="parameters"></a>Parametry  
 `__fstrArg`  
 `StringReference` Którego dane są używane do zainicjowania nowe wystąpienie.  
  
 `__strArg`  
 Wskaźnik do tablicy wartości char16 służy do inicjowania nowego wystąpienia.  
  
 `__lenArg`  
 Liczba elementów w `__strArg`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszą wersję tego konstruktora jest konstruktora domyślnego. Druga wersja inicjuje nowy `StringReference` wystąpienia klasy z obiektu określonego przez `__fstrArg` parametru. Trzeci i czwarty przeciążeń zainicjować nowe `StringReference` wystąpienia z tablicy wartości char16. char16 reprezentuje znaku tekst UNICODE 16-bitowych.  
  


  
## <a name="see-also"></a>Zobacz też  
 [Klasa platform::StringReference](../cppcx/platform-stringreference-class.md)