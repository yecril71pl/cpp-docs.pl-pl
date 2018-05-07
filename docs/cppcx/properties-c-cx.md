---
title: Właściwości (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 64c7bc56-3191-4cd5-bdf4-476d07d285d5
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6393b5e5849ab2198fa8d084c2c1d15838c69bdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="properties-ccx"></a>Właściwości (C + +/ CX)
Typy środowiska wykonawczego systemu Windows ujawniać publicznego danych jako właściwości. Kod klienta uzyskuje dostęp do właściwości, takie jak publiczny datamember. Wewnętrznie właściwość jest implementowany jako bloku, który zawiera metodę dostępu get i/lub metody dostępu set. Za pomocą metody dostępu, można wykonać dodatkowe czynności przed lub po pobraniu wartość, na przykład można zdarzenia lub sprawdzana jest poprawność.  
  
### <a name="remarks"></a>Uwagi  
 Wartość właściwości jest zawarta w zmiennej prywatnej — znane jako *magazynu zapasowego*— która jest taki sam typ jak właściwość. Właściwość może zawierać zarówno metody dostępu set, która przypisuje wartość do magazynu zapasowego, i metody dostępu get, który pobiera wartość magazynu zapasowego. Właściwość jest tylko do odczytu umożliwia tylko metody dostępu get, tylko do zapisu, jeśli zapewnia tylko metody dostępu set i odczytu/zapisu (można modyfikować) Jeśli zapewnia obu metod dostępu.  
  
 A *trivial* właściwość jest właściwością odczytu/zapisu, dla którego kompilator automatycznie implementuje metody dostępu i magazynu zapasowego. Nie masz dostępu do wdrożenia przez kompilator. Jednak można zadeklarować właściwości niestandardowych i jawnie deklarować jego metody dostępu i magazynu zapasowego. W ramach dostępu możesz wykonać wszelka logika, która jest wymagana, takich jak sprawdzanie poprawności danych wejściowych do metody dostępu set, obliczenia wartości od wartości właściwości, uzyskiwanie dostępu do bazy danych lub zdarzenie, gdy właściwość.  
  
 Gdy C + +/ CX klasy referencyjnej zostanie uruchomiony, pamięci jest zero zainicjowany przed wywołaniem konstruktora jego; w związku z tym wszystkie właściwości są przypisywane domyślną wartość zero lub nullptr punkcie deklaracji.  
  
### <a name="examples"></a>Przykłady  
 W poniższym przykładzie przedstawiono sposób deklarowanie i dostępu do właściwości. Pierwszą właściwością `Name`, nosi nazwę *trivial* właściwości ponieważ kompilator automatycznie generuje `set` dostępu, `get` metody dostępu i magazynu zapasowego.  
  
 Drugą właściwością `Doctor`, jest właściwością tylko do odczytu, ponieważ określa on *bloku właściwości* które jawnie deklaruje tylko `get` metody dostępu. Ponieważ zadeklarowano bloku właściwości, musisz jawnie zadeklarować magazynu zapasowego; oznacza to, że ciąg prywatnej ^ zmiennej `doctor_`. Zwykle właściwość tylko do odczytu po prostu zwraca wartość magazynu zapasowego. Tylko klasy można ustawić wartości magazynu zapasowego, zwykle w konstruktorze.  
  
 Właściwość trzeci `Quantity`, jest właściwością odczytu i zapisu, ponieważ deklaruje on bloku właściwości, który deklaruje zarówno `set` metody dostępu i `get` dostępu.  
  
 `set` Akcesor wykonuje test użytkownika ważność przypisaną wartość. W przeciwieństwie do języka C#, tutaj nazwę, a *wartość* jest tylko identyfikator parametru w `set` akcesor; nie jest słowem kluczowym. Jeśli *wartość* nie jest większa niż zero, jest zgłaszany Platform::InvalidArgumentException. W przeciwnym razie wartość przechowywania zapasowy `quantity_`, został zaktualizowany o przypisanej wartości.  
  
 Należy pamiętać, że właściwości nie można zainicjować na liście elementu członkowskiego. Oczywiście można zainicjować zmienne magazynu zapasowego na liście elementu członkowskiego.  
  
 [!code-cpp[cx_properties#01](../cppcx/codesnippet/CPP/cx_properties/class1.h#01)]  
  
## <a name="see-also"></a>Zobacz też  
 [System typów](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)