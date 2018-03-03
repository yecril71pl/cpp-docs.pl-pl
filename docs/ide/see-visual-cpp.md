---
title: '&lt;zobacz&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <see>
- see
dev_langs:
- C++
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15e1aedefe6d20c181ff208f76a61f49e15f5214
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltseegt-visual-c"></a>&lt;zobacz&gt; (Visual C++)
\<Zobacz > należy określić łącze znajdujących się w tekście. Użyj [ \<seealso >](../ide/seealso-visual-cpp.md) wskazująca tekstu, które mogą zostać wyświetlone w sekcji Zobacz też.  
  
## <a name="syntax"></a>Składnia  
  
```  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywoływania z bieżącym środowisku kompilacji.  Nazwę należy ująć w cudzysłów pojedynczym lub podwójnym.  
  
 Kompilator sprawdza, czy element podanego kodu istnieje i jest rozpoznawany jako `member` do nazwy elementu w danych wyjściowych XML.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluj z użyciem [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
 Zobacz [ \<podsumowania >](../ide/summary-visual-cpp.md) przykład przy użyciu \<zobacz >.  
  
 Kompilator Visual C++ podejmie próbę rozpoznawania odwołań cref w jednym przebiegu za pośrednictwem komentarzy do dokumentacji.  W związku z tym jeśli przy użyciu reguł wyszukiwania C++, symbol nie znaleziono przez kompilator, odwołanie zostanie oznaczona jako nierozwiązane. Zobacz [ \<seealso >](../ide/seealso-visual-cpp.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak możesz wprowadzić cref odwołanie do typu ogólnego, taki sposób, że kompilator będzie rozpoznać odwołania.  
  
```  
// xml_see_cref_example.cpp  
// compile with: /LD /clr /doc  
// the following cref shows how to specify the reference, such that,  
// the compiler will resolve the reference  
/// <see cref="C{T}">  
/// </see>  
ref class A {};  
  
// the following cref shows another way to specify the reference,   
// such that, the compiler will resolve the reference  
/// <see cref="C < T >"/>  
  
// the following cref shows how to hard-code the reference  
/// <see cref="T:C`1">  
/// </see>  
ref class B {};  
  
/// <see cref="A">  
/// </see>  
/// <typeparam name="T"></typeparam>  
generic<class T>  
ref class C {};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)