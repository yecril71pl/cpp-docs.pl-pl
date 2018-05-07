---
title: Kreator dodawania funkcji członkowskiej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.function.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Member Function Wizard [C++]
ms.assetid: 13b6defc-faa6-4d57-83db-9dd854cbea3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 488c7ca455b267a79b0d2906849596346a191792
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="add-member-function-wizard"></a>Kreator dodawania funkcji członkowskiej
Ten kreator dodaje deklaracji funkcji elementu członkowskiego do pliku nagłówka i implementacji funkcji elementu członkowskiego klasy zastępczej, do pliku implementacji dla wybranej klasy.  
  
 Po dodaniu funkcji członkowskiej za pomocą kreatora można edytować kodu w środowisku programistycznym.  
  
 **Zwracany typ**  
 Ustawia typ zwracany dla funkcji członkowskiej, który dodajesz. Możesz podać własne zwracany typ lub wybrać z listy dostępnych typów. Aby uzyskać informacje o typach, zobacz [podstawowych typów](../cpp/fundamental-types-cpp.md).  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned int`|  
|**double**|**long**|`unsigned long`|  
|**float**|**short**|`void`|  
|`HRESULT`|`unsigned char`||  
  
 **Nazwa funkcji**  
 Ustawia nazwę funkcji członkowskiej, który dodajesz.  
  
 **Typ parametru**  
 Ustawia typ parametru dodawanego do funkcji członkowskiej, jeśli funkcja członkowska ma następujące parametry. Możesz podać własne typ parametru lub wybrać z listy dostępnych typów.  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned char`|  
|**double**|**long**|`unsigned int`|  
|**float**|**short**|`unsigned long`|  
  
 **Nazwa parametru**  
 Ustawia nazwę parametru dodawanego do funkcji członkowskiej, jeśli funkcja członkowska ma następujące parametry.  
  
 **Listy parametrów**  
 Wyświetla listę parametrów, które zostały dodane do funkcji członkowskiej. Aby dodać parametr do listy, podaj typu i nazwy **typ parametru** i **Nazwa parametru** pola i kliknij przycisk **Dodaj**. Aby usunąć parametr z listy, wybierz parametr i kliknij przycisk **Usuń**.  
  
 **Dostęp**  
 Ustawia dostęp do funkcji członkowskiej. Modyfikatory dostępu są słów kluczowych, które Określ dostęp innych klas, że funkcja elementu członkowskiego. Zobacz [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md) Aby uzyskać więcej informacji na temat określania dostępu. Poziom dostępu do funkcji Członkowskich ustawiono **publicznego** domyślnie.  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 Sprawdź, czy nowych funkcji członkowskiej jest statyczny lub wirtualnych oraz czy jest wbudowany lub czystej. Jeśli ustawisz funkcji członkowskiej jako czysty, `Virtual` pole wyboru jest zaznaczone oraz **wbudowanego** pole wyboru jest niedostępny. Wartość domyślna to funkcja członkowska Niestatyczne, niewirtualna.  
  
|Opcja|Opis|  
|------------|-----------------|  
|[Static](../cpp/storage-classes-cpp.md)|Określa, że funkcja działa jak globalnym i może zostać wywołana poza klasy, nawet w przypadku nie wystąpienia klasy. Funkcja członkowska nie ma dostępu do niestatycznego elementów członkowskich. Funkcja członkowska określony jako `Static` nie może być wirtualny.|  
|[Wirtualny](../cpp/virtual-cpp.md)|Zapewnia, że funkcja poprawny element członkowski jest wywoływana dla obiektu, niezależnie od wyrażenia używane do tworzenia wywołań funkcji członkowskiej. Funkcja członkowska określony jako `Virtual` nie może być statyczna.|  
|**Czysty**|Wskazuje, że implementacja nie są udostępniane dla funkcji wirtualny element członkowski został zadeklarowany; w związku z tym **czystej** można określić tylko dla funkcji wirtualnych elementów członkowskich. Klasa, która zawiera co najmniej jeden czystej wirtualnej funkcji członkowskiej jest traktowany jako klasy abstrakcyjnej. Klasy pochodne klasy abstrakcyjnej klasy należy zaimplementować czystej wirtualnej funkcji członkowskiej lub są one, zbyt, klas abstrakcyjnych.|  
|[Wbudowany](../cpp/inline-functions-cpp.md)|Instruuje kompilator, aby wstawić kopię treści funkcji Członkowskich do każdego miejsca, gdy funkcja członkowska zostanie wywołana. Funkcja członkowska określony jako **wbudowanego** nie może być czystym.|  
  
 **plik .cpp**  
 Ustawia lokalizację pliku, w którym zapisywana jest implementacją funkcji elementu członkowskiego klasy zastępczej. Domyślnie jest ona zapisywana w pliku .cpp, do którego jest dodawana funkcja członkowska klasy. Kliknij przycisk wielokropka, aby zmienić nazwę pliku. Implementacja funkcji elementu członkowskiego jest dodawany do zawartość wybranego pliku.  
  
 **Komentarz**  
 Zawiera komentarz w pliku nagłówka dla funkcji Członkowskich.  
  
 **Podpis funkcji**  
 Wyświetla funkcji członkowskiej wyświetlaną w kodzie po kliknięciu **Zakończ**. Nie można edytować w tym polu. Aby zmienić funkcji członkowskiej, zmień odpowiednie pola w kreatorze.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)