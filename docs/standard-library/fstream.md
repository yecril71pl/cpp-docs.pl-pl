---
title: "&lt;fstream —&gt; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <fstream>
dev_langs: C++
helpviewer_keywords: fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d41719c7ff7ce2d7a906395ed65b891e2583bac8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltfstreamgt"></a>&lt;fstream —&gt;
Definiuje kilka klas, które obsługują operacje iostream sekwencji przechowywane w zewnętrznych plikach.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <fstream>  
  
```  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Typ `basic_filebuf` specjalne na `char` parametrów szablonu.|  
|[fstream —](../standard-library/fstream-typedefs.md#fstream)|Typ `basic_fstream` specjalne na `char` parametrów szablonu.|  
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Typ `basic_ifstream` specjalne na `char` parametrów szablonu.|  
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Typ `basic_ofstream` specjalne na `char` parametrów szablonu.|  
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Typ `basic_fstream` specjalne na `wchar_t` parametrów szablonu.|  
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Typ `basic_ifstream` specjalne na `wchar_t` parametrów szablonu.|  
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Typ `basic_ofstream` specjalne na `wchar_t` parametrów szablonu.|  
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Typ `basic_filebuf` specjalne na `wchar_t` parametrów szablonu.|  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[basic_filebuf —](../standard-library/basic-filebuf-class.md)|Klasa szablonu opisuje buforu strumienia, który kontroluje przekazywania elementów typu **elementu**, którego cech znaków są określane przez klasę **Tr**, do i z sekwencję elementy przechowywane w Plik zewnętrzny.|  
|[basic_fstream —](../standard-library/basic-fstream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje wstawiania i wyodrębniania elementów i obiektów zakodowany przy użyciu buforu strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)\<**elementu**,  **TR**>, elementami typu **elementu**, którego cech znaków są określane przez klasę **Tr**.|  
|[basic_ifstream —](../standard-library/basic-ifstream-class.md)|Klasy szablonów opisuje obiekt, który kontroluje wyodrębniania elementów i zakodowanego obiektów z buforu strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)\<**elementu**, **Tr**>, elementami typu **elementu**, którego cech znaków są określane przez klasę **Tr**.|  
|[basic_ofstream —](../standard-library/basic-ofstream-class.md)|Klasa szablonu opisuje obiekt, który kontroluje wstawiania elementów i obiektów zakodowanych do buforu strumienia klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md)\<**elementu**, **Tr**>, elementami typu **elementu**, którego cech znaków są określane przez klasę **Tr**.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)



