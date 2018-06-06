---
title: Klasa platform::Array | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Array Constructors
- VCCORLIB/Namespace not found::Platform::Array::Value
dev_langs:
- C++
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 65c45265714f869de10bdfd450c2b1349d6b526b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704675"
---
# <a name="platformarray-class"></a>Klasa platform::Array
Reprezentuje tablicę jednowymiarowa, można modyfikować, który jest odbierany i przekazywane przez interfejs binarne aplikacji (ABI).  
  
## <a name="syntax"></a>Składnia  
  
```cpp    
template <typename T>  
private ref class Array<TArg, 1> :   
    public WriteOnlyArray<TArg, 1>,  
    public IBoxArray<TArg>   
```  
  
### <a name="members"></a>Elementy członkowskie  
 Platform::Array dziedziczy wszystkie metody z [klasy Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) i implementuje `Value` właściwość [Platform::IBoxArray interfejsu](../cppcx/platform-iboxarray-interface.md).  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Konstruktory tablicy](#ctor)|Inicjuje tablicą jednowymiarową, można modyfikować typów określonej przez parametr szablonu klasy *T*.|  
  
### <a name="methods"></a>Metody  
 Zobacz [Platform::WriteOnlyArray klasy](../cppcx/platform-writeonlyarray-class.md).  
  
### <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|[Array::Value](#value)|Pobiera dojścia do bieżącej tablicy.|  
  
### <a name="remarks"></a>Uwagi  
 Klasa tablicy jest zapieczętowany i nie może być dziedziczona.  
  
 System typów środowiska wykonawczego systemu Windows nie obsługuje pojęcia Tablice nieregularne i dlatego nie można przekazać IVector < Platform::Array\<T >> jako parametr zwrotnego wartość lub metody. Aby przekazać tablicy nieregularnej lub sekwencję sekwencji między interfejsem ABI, należy użyć `IVector<IVector<T>^>`.  
  
 Aby uzyskać więcej informacji na temat sposobu używania Platform::Array, zobacz [tablicy i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
 System typów środowiska wykonawczego systemu Windows nie obsługuje pojęcia Tablice nieregularne i dlatego nie można przekazać IVector < Platform::Array\<T >> jako parametr zwrotnego wartość lub metody. Aby przekazać tablicy nieregularnej lub sekwencję sekwencji między interfejsem ABI, należy użyć `IVector<IVector<T>^>`.  
  
 Ta klasa jest zdefiniowana w nagłówku vccorlib.h, który jest automatycznie uwzględniany przez kompilator. Jest widoczna w funkcji IntelliSense, ale nie w przeglądarce obiektów, ponieważ nie jest typem publicznym zdefiniowanym w platform.winmd.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  

 
## <a name="ctor"></a>  Konstruktory tablicy
Inicjuje tablicą jednowymiarową, można modyfikować typów określonej przez parametr szablonu klasy *T*.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
Array(unsigned int size);  
Array(T* data, unsigned int size);    
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Parametr szablonu klasy.  
  
 `size`  
 Liczba elementów w tablicy.  
  
 `data`  
 Wskaźnik do tablicy danych typu `T` używany do zainicjowania obiektu tej tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat tworzenia wystąpień Platform::Array, zobacz [tablicy i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).

## <a name="get"></a>  Array::Get — metoda
Pobiera odwołanie do elementu tablicy w określonej lokalizacji indeksu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp    
T& get(unsigned int index)  const;  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 Liczony od zera indeks, który identyfikuje element w tablicy. Indeks minimalna jest równa 0, a maksymalna wartość indeksu jest wartość określoną przez `size` parametru w [konstruktora Array](#ctor).  
  
### <a name="return-value"></a>Wartość zwracana  
 Określony przez element tablicy `index` parametru.  
  
## <a name="value"></a>  Właściwość Array::Value
Pobiera dojścia do bieżącej tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp 
property Array^ Value;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do bieżącej tablicy.  

## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)   
 [Tablica i WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)