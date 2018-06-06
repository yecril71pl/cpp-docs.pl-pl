---
title: '&lt;SeeAlso&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <seealso>
- seealso
dev_langs:
- C++
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a726a2fa1694fd346a6632fdc5e40bd53547fc8
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33334311"
---
# <a name="ltseealsogt-visual-c"></a>&lt;SeeAlso&gt; (Visual C++)
\<Seealso > należy określić tekst, który ma być wyświetlane w sekcji Zobacz też. Użyj [ \<zobacz >](../ide/see-visual-cpp.md) można określić łącze od w tekście.  
  
## <a name="syntax"></a>Składnia  
  
```  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywoływania z bieżącym środowisku kompilacji.  Nazwę należy ująć w cudzysłów pojedynczym lub podwójnym.  
  
 Kompilator sprawdza, czy element podanego kodu istnieje i jest rozpoznawany jako `member` do nazwy elementu w danych wyjściowych XML.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.  
  
 Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../ide/see-visual-cpp.md).  
  
## <a name="remarks"></a>Uwagi  
 Kompiluj z użyciem [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
 Zobacz [ \<podsumowania >](../ide/summary-visual-cpp.md) przykład za pomocą \<seealso >.  
  
 Kompilator Visual C++ podejmie próbę rozpoznawania odwołań cref w jednym przebiegu za pośrednictwem komentarzy do dokumentacji.  W związku z tym jeśli przy użyciu reguł wyszukiwania C++, symbol nie znaleziono przez kompilator, odwołanie zostanie oznaczona jako nierozwiązane.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie cref odwołuje się nierozwiązane symbolu. Komentarz XML dla cref do B::Test będzie `<seealso cref="!:B::Test" />`, podczas gdy odwołanie do A::Test jest poprawnie sformułowanym `<seealso cref="M:A.Test" />`.  
  
```  
// xml_seealso_tag.cpp  
// compile with: /LD /clr /doc  
// post-build command: xdcmake xml_seealso_tag.dll  
  
/// Text for class A.  
public ref struct A {  
   /// <summary><seealso cref="A::Test"/>  
   /// <seealso cref="B::Test"/>  
   /// </summary>  
   void MyMethod(int Int1) {}  
  
   /// text  
   void Test() {}  
};  
  
/// Text for class B.  
public ref struct B {  
   void Test() {}  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)