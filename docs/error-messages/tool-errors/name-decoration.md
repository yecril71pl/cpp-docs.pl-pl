---
title: Nazwa Decoration | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e956d0acf9e6debcb183577775e2215e7eccec7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="name-decoration"></a>Nazwij dekorację
Nazwij dekorację zazwyczaj odwołuje się do konwencji nazewnictwa C++, ale można stosować do liczby przypadków C również. Domyślnie C++ używa nazwy funkcji, parametry oraz zwracany typ utworzyć konsolidatora nazwy funkcji. Należy wziąć pod uwagę następujących funkcji:  
  
```  
void CALLTYPE test(void)  
```  
  
 W poniższej tabeli przedstawiono nazwy konsolidatora dla różnych konwencji wywoływania.  
  
|Konwencja wywoływania|Plik zewnętrzny "C" lub .c|.cpp, .cxx lub /TP|  
|------------------------|---------------------------|------------------------|  
|Konwencja nazewnictwa C (`__cdecl`)|_testowy|? test @@ZAXXZ|  
|Konwencja nazewnictwa Fastcall (`__fastcall`)|@test@0|? test @@YIXXZ|  
|Standardowej konwencji nazewnictwa wywołania (`__stdcall`)|_test@0|? test @@YGXXZ|  
|Konwencja nazewnictwa Vectorcall (`__vectorcall`)|Testowanie @@0|? test @@YQXXZ|  
  
 Umożliwia wywoływanie funkcji C z C++ zewnętrzne "C". Zewnętrzne "C" wymusza na użytek konwencji nazewnictwa C funkcje języka C++ z systemem innym niż klasa. Należy pamiętać o przełączniki kompilatora **/TC** lub **/Tp**, który Poinformuj kompilator, aby zignorować rozszerzenie nazwy pliku i skompiluj plik jako języka C lub C++, odpowiednio. Te opcje mogą powodować nazw, które nie oczekuje.  
  
 Prototypy funkcji, które mają niezgodne parametry może również spowodować tego błędu. Nazwij dekorację dołącza parametry funkcji w nazwie końcowego ozdobione funkcji. Wywołanie funkcji z typami parametrów, które nie odpowiadają wartościom w deklaracji funkcji może spowodować LNK2001.  
  
 Nie istnieje obecnie standard dla nazw między dostawców kompilatora lub nawet między różnymi wersjami kompilatora języka C++. W związku z tym konsolidacji plików obiektu skompilowanego z inne kompilatory nie może utworzyć sam schemat nazewnictwa i w związku z tym powoduje nierozwiązane obiektów zewnętrznych.  
  
## <a name="see-also"></a>Zobacz też  
 [Błąd narzędzi konsolidatora LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)