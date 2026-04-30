Exercício 1 - Create

Criar banco
use loja_virtual

Criar coleção
db.createCollection("produtos")

Inserir um produto
db.produtos.insertOne({
  nome: "Smartphone Galaxy A15",
  categoria: "Eletronicos",
  preco: 1299.90,
  marca: "Samsung",
  armazenamento: "128GB",
  cor: "Azul"
})

Inserir vários produtos
db.produtos.insertMany([
  {
    nome: "MongoDB na Pratica",
    categoria: "Livros",
    preco: 79.90,
    autor: "Joao Silva",
    editora: "Tech Books",
    paginas: 320
  },
  {
    nome: "Camiseta Basica",
    categoria: "Roupas",
    preco: 49.90,
    tamanho: "M",
    cor: "Preta",
    material: "Algodao"
  },
  {
    nome: "Notebook Ultra X",
    categoria: "Eletronicos",
    preco: 3899.90,
    marca: "Lenovo",
    memoria_ram: "16GB",
    processador: "Intel i7"
  },
  {
    nome: "Tenis Runner Pro",
    categoria: "Calcados",
    preco: 299.90,
    tamanho: 42,
    cor: "Branco",
    marca: "Olympikus"
  }
])


Exercício 2 - Read

Listar todos os produtos
db.produtos.find()


Produtos com preço maior que 100
db.produtos.find({ preco: { $gt: 100 } })


Produtos da categoria Eletronicos
db.produtos.find({ categoria: "Eletronicos" })


Mostrar apenas nome e preço
db.produtos.find({}, { nome: 1, preco: 1, _id: 0 })


Exercício 3 - Update

Atualizar preço

db.produtos.updateOne(
  { nome: "Smartphone Galaxy A15" },
  { $set: { preco: 1199.90 } }
)
db.produtos.find({ nome: "Smartphone Galaxy A15" })


Adicionar estoque para todos

db.produtos.updateMany(
  {},
  { $set: { estoque: 10 } }
)
db.produtos.find()


Marcar roupas como promoção

db.produtos.updateMany(
  { categoria: "Roupas" },
  { $set: { promocao: true } }
)
db.produtos.find({ categoria: "Roupas" })

Exercício 4 - Delete

Remover um produto

db.produtos.deleteOne({ nome: "MongoDB na Pratica" })
db.produtos.find()


Remover categoria

db.produtos.deleteMany({ categoria: "Calcados" })
db.produtos.find()