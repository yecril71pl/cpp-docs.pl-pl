---
title: dllexport i dllimport | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dllimport_cpp
- dllexport_cpp
dev_langs:
- C++
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4e5b98b5541d1dc5f4a94c9611668a9ea8d787a
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport
**Microsoft Specific**  
  
 `dllexport` i **dllimport** atrybuty klasy magazynu są specyficzne dla firmy Microsoft przez rozszerzenia języków C i C++. Można używać ich do eksportowania i importowania obiektów, danych i funkcji do lub z biblioteki DLL.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
   __declspec( dllimport ) declarator  
   __declspec( dllexport ) declarator  
```  
  
## <a name="remarks"></a>Uwagi  
 Te atrybuty jawnie definiować interfejsu biblioteki DLL do klienta, który może być pliku wykonywalnego lub innej bibliotece DLL. Deklarowanie funkcji jako `dllexport` eliminuje potrzebę stosowania pliku definicji modułu (.def), co najmniej względem specyfikacji wyeksportowanej funkcji. `dllexport` Atrybutu zastępuje `__export` — słowo kluczowe.  
  
 Jeśli klasa jest oznaczona declspec(dllexport), wszelkie specjalizacje szablonów klas w hierarchii klasy niejawnie są oznaczone jako declspec(dllexport). Oznacza to, że szablonów klas jawnie są tworzone i elementów członkowskich klasy musi być zdefiniowany.  
  
 `dllexport`funkcji udostępnia funkcję z nazwy ozdobione. Dla funkcji języka C++ w tym przekręcona nazwa. Funkcje języka C lub funkcje, które są zadeklarowane jako `extern "C"`, w tym decoration specyficzne dla platformy, który bazuje na Konwencja wywoływania. Aby uzyskać informacje na nazwij dekorację w kodzie C/C++, zobacz [dekorowane nazwy](../build/reference/decorated-names.md). Nie nazwij dekorację jest stosowany do wyeksportowanej funkcji języka C lub C++ `extern "C"` funkcji przy użyciu `__cdecl` konwencji wywoływania.  
  
 Aby wyeksportować bez nazwy, można połączyć się przy użyciu pliku definicji modułu (.def), który definiuje nazwę bez w sekcji eksportu. Aby uzyskać więcej informacji, zobacz [EKSPORTÓW](../build/reference/exports.md). Inny sposób, aby wyeksportować bez nazwy jest użycie `#pragma comment(linker, "/export:alias=decorated_name")` dyrektywy w kodzie źródłowym.  
  
 Gdy zadeklarować `dllexport` lub **dllimport**, należy użyć [rozszerzona Składnia atrybutu](../cpp/declspec.md) i `__declspec` — słowo kluczowe.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// Example of the dllimport and dllexport class attributes  
__declspec( dllimport ) int i;  
__declspec( dllexport ) void func();  
```  
  
 Alternatywnie aby zwiększyć czytelność kodu, można użyć definicje makr:  
  
```cpp  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllImport int j;  
DllExport int n;  
```  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Definicje i deklaracje](../cpp/definitions-and-declarations-cpp.md)  
  
-   [Definiowanie funkcji śródwierszowych języka C++ z dllexport i dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
-   [Ograniczenia i reguły ogólne](../cpp/general-rules-and-limitations.md)  
  
-   [Korzystanie z dllimport i dllexport w klasach C++](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)