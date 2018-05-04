---
title: volatile (c) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- volatile_cpp
dev_langs:
- C++
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 295654586a3fe251526a4764d54f80f3a70c7014
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="volatile-c"></a>volatile (C++)
Kwalifikator typu można użyć, aby zadeklarować, że obiekt może być modyfikowany w programie przez sprzęt.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
volatile declarator ;  
```  
  
## <a name="remarks"></a>Uwagi  
 Można użyć [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) przełącznika kompilatora, aby zmodyfikować interpretowanie kompilator to słowo kluczowe.  
  
 Visual Studio interpretuje `volatile` — słowo kluczowe inaczej w zależności od architektury docelowej. Dla ARM, jeśli nie **/volatile** określono opcję kompilatora, wykonuje kompilator tak, jakby **/volatile:iso** zostały określone. Architektur innych niż ARM, jeśli nie **/volatile** określono opcję kompilatora, wykonuje kompilator tak, jakby **/volatile:ms** określono; w związku z tym dla architektur innych niż ARM firma Microsoft zdecydowanie Zalecamy, aby w przypadku określenia **/volatile:iso**, używanie jawna synchronizacja elementów podstawowych i funkcje wewnętrzne kompilatora, jeśli mamy do czynienia pamięci, który jest współużytkowany przez wątki.  
  
 Można użyć `volatile` kwalifikator w celu zapewnienia dostępu do lokalizacji pamięci, które są używane przez procesy asynchronicznego, takie jak programy obsługi przerwań.  
  
 Gdy `volatile` jest używany w zmiennej, która ma również [__restrict](../cpp/extension-restrict.md) — słowo kluczowe, `volatile` ma pierwszeństwo.  
  
 Jeśli `struct` elementu członkowskiego jest oznaczony jako `volatile`, następnie `volatile` są propagowane w strukturze całego. Jeśli struktura nie ma długości, która może zostać skopiowana na bieżącej architektury za pomocą jednej instrukcji `volatile` mogą zostać utracone całkowicie na tej struktury.  
  
 `volatile` — Słowo kluczowe może nie mają wpływu na pole, jeśli jest spełniony jeden z następujących warunków:  
  
-   Długość pola nietrwałego przekracza maksymalny rozmiar, który można skopiować na bieżącej architektury za pomocą jednej instrukcji.  
  
-   Długość peryferyjnych zawierający `struct`— lub jeśli jest ono członkiem prawdopodobnie zagnieżdżonych `struct`— przekracza maksymalny rozmiar, który można skopiować na bieżącej architektury za pomocą jednej instrukcji.  
  
 Mimo że procesor nie zmienić kolejność uzyskuje dostęp do pamięci bez buforowalnej, zmienne bez buforowalnej musi być oznaczona jako `volatile` aby zagwarantować, że kompilator nie zmienić kolejność pamięć uzyskuje dostęp.  
  
 Obiekty, które są zadeklarowane jako `volatile` nie są używane w niektórych optymalizacji, ponieważ ich wartości można zmienić w dowolnym momencie.  System ma zawsze wartość bieżącą wartość obiektu volatile żądanie, nawet jeśli poprzednie instrukcji wyświetlony monit o podanie wartości z tego samego obiektu.  Ponadto wartość obiektu jest zapisywane bezpośrednio na przypisania.  
  
## <a name="iso-compliant"></a>ISO zgodne  
 Zapoznać się z kluczowego volatile C# lub zapoznać się z zachowaniem `volatile` we wcześniejszych wersjach programu Visual C++, należy pamiętać, że C ++ 11 normy ISO `volatile` — słowo kluczowe jest inna i jest obsługiwany w programie Visual Studio po [/ volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md) określono opcję kompilatora. (Dla ARM, określono domyślnie). `volatile` — Słowo kluczowe języka C ++ 11 kodu normy ISO ma być używany tylko w przypadku dostępu do sprzętu; nie należy używać do komunikacji między wątku. Do komunikacji między wątku używa mechanizmów takich jak [std::atomic\<T >](../standard-library/atomic.md) z [standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md).  
  
## <a name="end-of-iso-compliant"></a>Koniec ISO zgodne  
  
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Gdy **/volatile:ms** jest używana opcja kompilatora — domyślnie, gdy są przeznaczone dla architektury niż ARM — kompilator generuje dodatkowy kod w celu zachowania kolejności między odwołania do obiektów volatile oprócz obsługi kolejność odwołań do innych obiektów globalnych. W szczególności:  
  
-   Zapis do obiektów volatile (znanej także jako nietrwałe zapisu) ma semantykę wersji; oznacza to, że odwołanie do obiektu globalnych lub statycznych, które występują przed zapisu do obiektu volatile w sekwencji instrukcji nastąpi przed tym volatile zapisu w skompilowanym plikiem binarnym.  
  
-   Odczytu obiektu volatile (znanej także jako odczytu volatile) ma semantykę pobierania; oznacza to, że odwołanie do obiektu globalnej lub statycznej, występujący po odczytu volatile pamięci w sekwencji instrukcji następuje po tym volatile odczytu w skompilowanym plikiem binarnym.  
  
 Dzięki temu obiekty nietrwałe służący do blokowania pamięci i zwalnia w aplikacjach wielowątkowych.  
  
> [!NOTE]
>  Gdy jest zależne od rozszerzonej gwarancji, że została podana podczas **/volatile:ms** jest używana opcja kompilatora, kod jest nieprzenośne.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Keywords](../cpp/keywords-cpp.md)   
 [Const](../cpp/const-cpp.md)   
 [Wskaźniki stałe i nietrwałe](../cpp/const-and-volatile-pointers.md)