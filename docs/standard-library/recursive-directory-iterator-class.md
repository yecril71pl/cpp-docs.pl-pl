---
title: "recursive_directory_iterator — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: filesystem/std::tr2::sys::recursive_directory_iterator
dev_langs: C++
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 55e44e447ee8ad2e449c46acb5535a41346fd19f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator — klasa
w tym artykule opisano wejściowych iteratora który sekwencji za pomocą nazwy plików w katalogu, prawdopodobnie malejącej do podkatalogów rekursywnie. Dla iteratora X, wyrażenie * X ocenia się do obiektu directory_entry — klasa, która opakowuje nazwę pliku i wszystkie znane o jej stanie.  
  
 Aby uzyskać więcej informacji oraz przykłady kodu, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
class recursive_directory_iterator;  
```  
  
## <a name="remarks"></a>Uwagi  
 Szablon klasy magazynów:  
  
1.  obiekt typu stosu < pary\<directory_iterator —, ścieżka >>, nazywany mystack tutaj na potrzeby specyfikacją reprezentuje zagnieżdżania katalogów można sekwencjonowania  
  
2.  w tym miejscu myentry, reprezentujący bieżącej nazwy pliku w sekwencji katalog o nazwie obiektu directory_entry — typ  
  
3.  obiekt typu bool, nazywany no_push w tym miejscu, który rejestruje, czy spadku cykliczne do podkatalogów jest wyłączone  
  
4.  Obiekt directory_options — typu, o nazwie myoptions w tym miejscu, który rejestruje opcje ustalone w konstrukcji  
  
 Domyślne skonstruowany obiektu typu recursive_directory_entry ma iteratora sekwencja kończenia mystack.top .first () i reprezentuje iteratora sekwencja kończenia. Na przykład, dla danego katalogu abc wpisy def (katalog), def/ghi i jkl, kod:  
  
```  
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)  
    visit(next->path());
```  
  
 Wywołanie odwiedzi z argumentami `path("abc/def/ghi") and path("abc/jkl").`kwalifikujesz sekwencjonowania za pośrednictwem poddrzewa katalogu na dwa sposoby:  
  
1.  Łącza symbolicznego katalog ma zostać przeprowadzone skanowanie tylko wtedy, gdy skonstruować recursive_directory_iterator — z argumentem directory_options —, którego wartość jest directory_options::follow_directory_symlink.  
  
2.  Jeśli wywołujesz disable_recursion_pending następnie kolejnych katalogu podczas przyrostu nie będzie rekursywnie skanowania.  
  
## <a name="recursivedirectoryiteratordepth"></a>recursive_directory_iterator::DEPTH  
  
```  
int depth() const;
```  
  
 Zwraca mystack.size() - 1, tak aby pval przy głębokości zero.  
  
## <a name="recursivedirectoryiteratordisablerecursionpending"></a>recursive_directory_iterator::disable_recursion_pending  
  
```  
void disable_recursion_pending();
```  
  
 Funkcja członkowska przechowuje wartość true w no_push.  
  
## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator! =  
  
```  
bool operator!=(const recursive_directory_iterator& right) const;
```  
  
 Zwraca element członkowski operatora! (* to == prawej strony).  
  
## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator =  
  
```  
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;  
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;  
```  
  
 Operatory przypisania domyślnego elementu członkowskiego działają zgodnie z oczekiwaniami.  
  
## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator ==  
  
```  
bool operator==(const recursive_directory_iterator& right) const;
```  
  
 Operator członkowski zwraca wartość true tylko wtedy, gdy oba * to oraz prawo Iteratory sekwencja kończenia lub obie są nie end elementu sekwencji — Iteratory.  
  
## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator *  
  
```  
const directory_entry& operator*() const;
```  
  
 Operator członkowski zwraca myentry.  
  
## <a name="recursivedirectoryiteratoroperator-"></a>recursive_directory_iterator::operator ->  
  
```  
const directory_entry * operator->() const;
```  
  
 Zwraca & ** to.  
  
## <a name="recursivedirectoryiteratoroperator"></a>recursive_directory_iterator::operator ++  
  
```  
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```  
  
 Pierwszy funkcji członkowskiej wywołuje increment(), a następnie zwraca * to. Drugi funkcji członkowskiej tworzy kopię obiektu, wywołuje increment(), a następnie zwraca kopii.  
  
## <a name="recursivedirectoryiteratoroptions"></a>recursive_directory_iterator::Options  
  
```  
directory_options options() const;
```  
  
 Zwraca myoptions.  
  
## <a name="recursivedirectoryiteratorpop"></a>recursive_directory_iterator::POP  
  
```  
void pop();
```  
  
 Jeśli depth() == 0 obiekt staje się iteratora sekwencja kończenia. W przeciwnym razie funkcja członkowska kończy skanowanie bieżącego katalogu (najgłębszym) i wznawia przy następnym głębokości dolnej.  
  
## <a name="recursivedirectoryiteratorrecursionpending"></a>recursive_directory_iterator::recursion_pending  
  
```  
bool recursion_pending() const;
```  
  
 Zwraca! no_push.  
  
## <a name="recursivedirectoryiteratorrecursivedirectoryiterator"></a>recursive_directory_iterator::recursive_directory_iterator  
  
```  
recursive_directory_iterator() noexcept;  
explicit recursive_directory_iterator(const path& pval);

recursive_directory_iterator(const path& pval,  
    error_code& ec) noexcept;  
recursive_directory_iterator(const path& pval,  
    directory_options opts);

recursive_directory_iterator(const path& pval,  
    directory_options opts,  
    error_code& ec) noexcept;  
recursive_directory_iterator(const recursive_directory_iterator&) = default;  
recursive_directory_iterator(recursive_directory_iterator&&) noexcept = default;  
```  
  
 Pierwszy konstruktora tworzy iteratora sekwencja kończenia. Konstruktory drugiego i trzeciego przechowywania false w no_push i directory_options::none w myoptions, a następnie spróbuj otwierać i odczytywać pval jako katalog. W przypadku powodzenia zainicjować mystack i myentry do wyznaczenia pierwszy filename z systemem innym niż katalog w zagnieżdżonych sekwencji; w przeciwnym razie wygenerowanie iteratora sekwencja kończenia.  
  
 Konstruktory czwartym i piątym działają tak samo, jak drugi i trzecie, z wyjątkiem tego, że najpierw zapisać zdecyduje myoptions. Domyślne construtors działają zgodnie z oczekiwaniami.  
  
## <a name="recursivedirectoryiteratorincrement"></a>recursive_directory_iterator::Increment  
  
```  
recursive_directory_iterator& increment(error_code& ec) noexcept;  
```  
  
 Funkcja próbuje przejść do następnej nazwy pliku w zagnieżdżonych sekwencji. W przypadku powodzenia przechowuje nazwę tego pliku w myentry; w przeciwnym razie tworzy iteratora sekwencja kończenia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<filesystem >  
  
 **Namespace:** std::tr2::sys  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<FileSystem >](../standard-library/filesystem.md)   
 [Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md)

