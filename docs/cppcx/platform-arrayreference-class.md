---
title: Klasa platform::ArrayReference | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
dev_langs:
- C++
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8e4183c400cf45a23f24a98292b68f6df537da1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="platformarrayreference-class"></a>Klasa platform::ArrayReference
`ArrayReference` jest typem optymalizacji, który można podstawić [Platform::Array ^](../cppcx/platform-array-class.md) w parametrów wejściowych, gdy chcesz wypełnić tablicy stylu języka C z danych wejściowych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
class ArrayReference  
```
  
### <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ArrayReference::ArrayReference](#ctor)|Inicjuje nowe wystąpienie klasy `ArrayReference` klasy.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ArrayReference::operator() Operator](#operator-call)|Konwertuje to `ArrayReference` do `Platform::Array<T>^*`.|  
|[ArrayReference::operator = — Operator](#operator-assign)|Przypisuje zawartość innego `ArrayReference` do tego wystąpienia.|  
  
## <a name="exceptions"></a>Wyjątki  
  
### <a name="remarks"></a>Uwagi  
 Za pomocą `ArrayReference` do wypełnienia tablicy stylu języka C, można uniknąć operacji kopiowania dodatkowe, który będzie używany w funkcji kopiowania najpierw do `Platform::Array` zmiennej, a następnie w stylu języka C tablicy. Jeśli używasz `ArrayReference`, istnieje tylko jedna kopia operacji. Na przykład kod, zobacz [tablicy i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Nagłówek:** vccorlib.h  
  
## <a name="ctor"></a>  Konstruktor ArrayReference::ArrayReference
Inicjuje nowe wystąpienie klasy [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) klasy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);  
ArrayReference(ArrayReference&& otherArg)  
  
```  
  
### <a name="parameters"></a>Parametry  
 `dataArg`  
 Wskaźnik do tablicy danych.  
  
 `sizeArg`  
 Liczba elementów w tablicy źródłowej.  
  
 `otherArg`  
 `ArrayReference` Obiektu, którego dane zostaną przeniesione do zainicjowania nowego wystąpienia.  
  
### <a name="remarks"></a>Uwagi  
  


## <a name="operator-assign"></a>  ArrayReference::operator = — Operator
Przypisuje określony obiekt do bieżącego [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) obiektu za pomocą semantyki przenoszenia.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
ArrayReference& operator=(ArrayReference&& otherArg);  
  
```  
  
### <a name="parameters"></a>Parametry  
 `otherArg`  
 Obiekt, który jest przenoszony do bieżącego `ArrayReference` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu typu `ArrayReference`.  
  
### <a name="remarks"></a>Uwagi  
 `Platform::ArrayReference` to standard C++ szablon klasy, nie klasy referencyjnej.  
  


## <a name="operator-call"></a>  ArrayReference::operator() Operator
Konwertuje bieżący [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) wstecz do obiektu [Platform::Array](../cppcx/platform-array-class.md) klasy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
Array<TArg>^ operator ();  
  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do obiektu typu `Array<TArg>^`  
  
### <a name="remarks"></a>Uwagi  
 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) i [Platform::Array](../cppcx/platform-array-class.md) są standardowe szablony klas C++, ref nie klasy.  
  


  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)