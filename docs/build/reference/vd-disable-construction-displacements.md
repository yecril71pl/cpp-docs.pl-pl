---
title: -vd (Wyłącz przemieszczanie konstrukcji) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vd
dev_langs:
- C++
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e983da4521db077235c2b879e0d1277b9505e94
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605871"
---
# <a name="vd-disable-construction-displacements"></a>/vd (Wyłącz przemieszczanie konstrukcji)
## <a name="syntax"></a>Składnia  
  
```  
/vdn  
```  
  
## <a name="arguments"></a>Argumenty  
 `0`  
 Pomija elementu członkowskiego przemieszczenia konstruktora/destruktora vtordisp. Wybierz tę opcję tylko wtedy, gdy masz pewność, wszystkie konstruktory i destruktory klas wywołanie wirtualnej działa praktycznie.  
  
 `1`  
 Umożliwia tworzenie elementów członkowskich przemieszczenia konstruktora/destruktora vtordisp ukryte. Ten wybór jest ustawieniem domyślnym.  
  
 `2`  
 Pozwala na używanie [dynamic_cast Operator](../../cpp/dynamic-cast-operator.md) na obiekcie, który jest konstruowany. Na przykład dynamic_cast z wirtualnej klasy bazowej do klasy pochodnej.  
  
 **/ vd2** dodaje pole vtordisp, gdy baza wirtualna z funkcjami wirtualnymi. **/ vd1** powinny być wystarczające. Najczęściej zamierzone, gdzie **/vd2** jest niezbędne jest, gdy funkcja tylko wirtualna w sieci wirtualnej podstawowym destruktora.  
  
## <a name="remarks"></a>Uwagi  
 Te opcje są stosowane tylko dla kodu C++, który korzysta z baz wirtualnych.  
  
 Visual C++ implementuje obsługi przemieszczenia konstrukcji języka C++ w sytuacjach, gdzie używane jest wirtualne dziedziczenie. Przemieszczanie konstrukcji rozwiązać problem utworzony, jeśli funkcja wirtualna, zadeklarowanej w wirtualnej podstawowej i przesłonięcia w klasie pochodnej, jest wywoływana z konstruktora podczas konstruowania dalsze klasę pochodną.  
  
 Problem polega na to, czy funkcja wirtualna może być przekazywane do nieprawidłowych `this` wskaźnika w wyniku rozbieżności między przemieszczanie do wirtualnego podstaw klasę i przemieszczanie się jej klas pochodnych. Rozwiązanie udostępnia dostosowanie przemieszczenia pojedynczego konstrukcji, dla każdego wirtualnego podstawy klasę o nazwie polem vtordisp.  
  
 Domyślnie vtordisp — pola zostały wprowadzone, zawsze wtedy, gdy kod definiuje zdefiniowanych przez użytkownika konstruktorów i destruktorów i zastępuje również funkcji wirtualnych z bazami wirtualnymi.  
  
 Te opcje dotyczą całych plików źródłowych. Użyj [vtordisp](../../preprocessor/vtordisp.md) do pominięcia i ponownego włączenia pól vtordisp działające na zasadzie klasa po klasie.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** stronę właściwości.  
  
4.  Wpisz opcje kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)