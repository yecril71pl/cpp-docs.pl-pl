---
title: '&lt;fstream —&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <fstream>
dev_langs:
- C++
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fe86803f986853335fbad15e0c3323d9365d381
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

Definiuje kilka klas, które obsługują operacje iostream sekwencji przechowywane w zewnętrznych plikach.

## <a name="syntax"></a>Składnia

```cpp
#include <fstream>

```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Typ `basic_filebuf` specjalne na `char` parametrów szablonu.|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|Typ `basic_fstream` specjalne na `char` parametrów szablonu.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Typ `basic_ifstream` specjalne na `char` parametrów szablonu.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Typ `basic_ofstream` specjalne na `char` parametrów szablonu.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Typ `basic_fstream` specjalne na `wchar_t` parametrów szablonu.|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Typ `basic_ifstream` specjalne na `wchar_t` parametrów szablonu.|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Typ `basic_ofstream` specjalne na `wchar_t` parametrów szablonu.|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Typ `basic_filebuf` specjalne na `wchar_t` parametrów szablonu.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|Klasa szablonu opisuje buforu strumienia, który kontroluje przekazywania elementów typu **elementu**, którego cech znaków są określane przez klasę **Tr**, do i z sekwencję elementy przechowywane w Plik zewnętrzny.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje wstawiania i wyodrębniania elementów i obiektów zakodowany przy użyciu buforu strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)\<**elementu**,  **TR**>, elementami typu **elementu**, którego cech znaków są określane przez klasę **Tr**.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|Klasy szablonów opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowanego obiektów z buforu strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)\<**elementu**, **Tr**>, elementami typu **elementu**, którego cech znaków są określane przez klasę **Tr**.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje wstawiania elementów i obiektów zakodowanych do buforu strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)\<**elementu**, **Tr**>, elementami typu **elementu**, którego cech znaków są określane przez klasę **Tr**.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
