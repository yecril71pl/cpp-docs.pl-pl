---
title: Partial (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- partial_CPP
dev_langs:
- C++
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd2debe47b0c60907c1a75f4e8b96d227468a345
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="partial--c-component-extensions"></a>częściowy (C++ Component Extensions)
`partial` — Słowo kluczowe umożliwia różnych części klasy ref do utworzenia niezależnie i w różnych plikach.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 (Ta funkcja językowa dotyczy tylko środowiska uruchomieniowego systemu Windows).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Dla klasy ref, który ma dwie definicje częściowe `partial` — słowo kluczowe jest stosowany do pierwszego wystąpienia definicji, a jest to zazwyczaj wykonywane przez automatycznie wygenerowany kod, tak aby człowieka koder nie użyj słowa kluczowego bardzo często. Dla wszystkich kolejnych definicji częściowej klasy, Pomiń `partial` modyfikator z *klucz klasy* identyfikator — słowo kluczowe i klasy. Gdy kompilator napotka klasy ref uprzednio zdefiniowany i identyfikator klasy, ale nie `partial` — słowo kluczowe, wszystkie części definicji klasy ref w jednej definicji wewnętrznie łączy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
partial class-key identifier {  
   /* The first part of the partial class definition. 
      This is typically auto-generated */  
}  
// ...  
class-key identifier {  
   /* The subsequent part(s) of the class definition. The same 
      identifier is specified, but the "partial" keyword is omitted. */  
}  
```  
  
### <a name="parameters"></a>Parametry  
 *klucz klasy*  
 Słowo kluczowe, który deklaruje klasy lub struktury, która jest obsługiwana przez środowisko wykonawcze systemu Windows. Albo `ref class`, `value class`, `ref struct`, lub `value struct`.  
  
 *Identyfikator*  
 Nazwa zdefiniowanego typu.  
  
### <a name="remarks"></a>Uwagi  
 Klasy częściowej obsługuje scenariusze, w którym można zmodyfikować jedną część definicję klasy w jednym pliku i automatyczne generowanie kodu oprogramowania — na przykład projektanta XAML — modyfikuje kodu w tej samej klasie w innym pliku. Przy użyciu klasy częściowej, można zapobiec zastępowaniu kodu generatora kodu automatyczne. W projekcie programu Visual Studio `partial` modyfikator jest automatycznie stosowane do wygenerowanego pliku.  
  
 Zawartość: Z dwoma wyjątkami definicji częściowej klasy może zawierać wszystkich elementów, które mogą zawierać definicji klasy pełne, jeśli `partial` — słowo kluczowe został pominięty. Jednak nie można określić klasy ułatwień dostępu (na przykład `public partial class X { ... };`), lub `declspec`.  
  
 Używane w definicji klasy częściowej specyfikatory dostępu *identyfikator* nie ma wpływu na dostępność domyślne w definicji kolejnych klasy częściowe lub pełne *identyfikator*. Wbudowany definicji statycznych elementów członkowskich danych są dozwolone.  
  
 Deklaracja: Częściową definicją klasy *identyfikator* tylko wprowadza nazwę *identyfikator*, ale *identyfikator* nie można używać w taki sposób, który wymaga klasy Definicja. Nazwa *identyfikator* nie może służyć wiedzieć, rozmiar *identyfikator*, lub Użyj podstawowego lub członek *identyfikator* aż po pełnej definicji napotka kompilatora *identyfikator*.  
  
 Liczba i kolejność: może być zero lub więcej definicji częściowej klasy dla *identyfikator*. Każdej definicji klasy częściowej *identyfikator* lexically musi poprzedzać jedna definicja pełne *identyfikator* (jeśli istnieje pełnej definicji; w przeciwnym razie klasa nie można użyć z wyjątkiem tak, jakby Deklaracja do przodu), ale nie muszą poprzedzać do przodu deklaracje *identyfikator*. Wszystkie klucze klasy muszą być zgodne.  
  
 Pełnej definicji: w punkcie pełnej definicji klasy *identyfikator*, zachowanie jest takie samo tak, jakby definicji *identyfikator* była zadeklarowana wszystkie klasy podstawowe elementy członkowskie, itp. w kolejności, w którym zostały one napotkano i określonych w klas częściowych.  
  
 Szablony: Częściowej klasy nie może być szablonem.  
  
 Ogólne: Częściowej klasy mogą być ogólnego pełnej definicji może być rodzajowy. Ale co klasy częściowe i pełne musi być dokładnie takie same ogólne parametry, łącznie z nazwami formalnych parametrów.  
  
 Aby uzyskać więcej informacji o sposobie używania `partial` — słowo kluczowe, zobacz [klasy częściowe (C + +/ CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
 (Ta funkcja językowa nie ma zastosowania do środowisko uruchomieniowe języka wspólnego).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy częściowe (C + +/ CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)