# **Pytest Decoratorları**

'Pytest', Python dilinde yazılmış bir test çerçevesi (framework)'dir. Bu çerçeve test alanında çalışma yapanlara yazdıkları testleri özelleştirme ve kolaylık sunar. Decorator'lar aracılığıyla test fonksiyonlarının davranışlarını şekillendirebilir. İşte 'pytest' kütüphanesinde kullanılan bazı temel decorator'lar:

## `@pytest.fixture`: Kaynakları Paylaşma ve Durum Yönetimi

`@pytest.fixture` decorator'ü, bir test fonksiyonuna eklendiğinde, o fonksiyonun bir _fixture_ olduğunu belirtir. _Fixturelar_, test fonksiyonları arasında paylaşılan kaynakları veya durumları temsil ederler. Bu, test verilerini sağlama, veritabanı bağlantıları oluşturma veya önceden koşulları belirleme gibi işlevselliği uygulamak için ideal bir mekanizmadır.
  
    
    import pytest
    @pytest.fixture
    def example_fixture():
        return "example data"
    
    def test_example(example_fixture):
        assert example_fixture == "example data"`
## `@pytest.mark`: Testleri İşaretleme ve Kategorize Etme

`@pytest.mark` decorator'ü, testlere özel işaretleme eklemek için kullanılır. Bu, belirli testleri gruplandırmak, koşullu olarak çalıştırmak veya diğer özel işlevleri gerçekleştirmek için kullanışlıdır. İşaretlemeler, test süitlerini düzenleme ve raporlama süreçlerini geliştirmede etkili bir araçtır.


    import pytest
    
    @pytest.mark.smoke
    def test_smoke():
        assert True
    
    @pytest.mark.slow
    def test_slow():
        assert True 

## `@pytest.mark.parametrize`: Parametreli Testler

`@pytest.mark.parametrize` decorator'ü, bir test fonksiyonunu farklı parametre setleriyle birden çok kez çalıştırmak için kullanılır. Bu, aynı test mantığını farklı giriş verileriyle tekrar tekrar kullanma yeteneği sağlar.

    import pytest
    
    @pytest.mark.parametrize("input, expected", [(1, 2), (2, 4), (3, 6)])
    def test_multiply_by_two(input, expected):
        result = input * 2
        assert result == expected

 

## `@pytest.mark.xfail`: Beklenen Başarısız Testler

`@pytest.mark.xfail` decorator'ü, bir testin bilerek başarısız olmasını beklemek için kullanılır. Test başarısız olsa da, bu durum bir sorun olarak ele alınmaz ve raporlanır.


    import pytest
    
    @pytest.mark.xfail
    def test_expected_to_fail():
        assert False

## `@pytest.mark.skip`: Testleri Atlama

`@pytest.mark.skip` decorator'ü, bir testin geçici olarak atlanmasını sağlar. Bu, testin geçici olarak devre dışı bırakılması gerektiğinde veya bir hata düzeltildiğinde kullanışlıdır.

    import pytest
    
    @pytest.mark.skip
    def test_skip_this():
        assert True

 

Bu decorator'lar, `pytest` çerçevesinin test yazma sürecini esnek ve özelleştirilebilir hale getirmesine olanak tanıyan güçlü araçlardır. Daha fazla bilgi için [pytest dokümantasyonunu](https://docs.pytest.org/en/stable/contents.html) inceleyebilirsiniz.
