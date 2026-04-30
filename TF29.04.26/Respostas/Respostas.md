# Create

// Seleciona (ou cria) o banco de dados
use("loja_virtual")

// Cria a coleção chamada "produtos"
db.createCollection("produtos")



# Insert


// Insere um único produto (smartphone)
db.produtos.insertOne({
  nome: "Smartphone Galaxy A15",
  categoria: "Eletronicos",
  preco: 1299.90,
  marca: "Samsung",
  armazenamento: "128GB",
  cor: "Azul"
})

// Insere vários produtos de categorias diferentes
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
  }
])



# Read


// Lista todos os produtos da coleção
db.produtos.find()

// Busca produtos com preço maior que 100
db.produtos.find({ preco: { $gt: 100 } })

// Lista apenas produtos da categoria "Eletronicos"
db.produtos.find({ categoria: "Eletronicos" })

// Retorna apenas os campos "nome" e "preco" (sem o _id)
db.produtos.find({}, { nome: 1, preco: 1, _id: 0 })

# Update 

// Atualiza o preço de um produto específico
db.produtos.updateOne(
  { nome: "Smartphone Galaxy A15" },
  { $set: { preco: 1199.90 } }
)

// Adiciona o campo "estoque" para TODOS os produtos
db.produtos.updateMany(
  {},
  { $set: { estoque: 50 } }
)

// Marca os produtos da categoria "Roupas" como estando em promoção
db.produtos.updateMany(
  { categoria: "Roupas" },
  { $set: { promocao: true } }
)


# Delete

// Remove um produto específico
db.produtos.deleteOne({ nome: "Camiseta Basica" })

// Remove todos os produtos da categoria "Livros"
db.produtos.deleteMany({ categoria: "Livros" })

