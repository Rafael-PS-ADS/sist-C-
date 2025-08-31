using System;
using System.Collections.Generic;

namespace SistemaProdutos
{
    class Program
    {
        static string produto1 = "Notebook";
        static string produto2 = "Smartphone";
        static string produto3 = "Tablet";

        static List<string> produtosEstoque = new List<string> { produto1, produto2, produto3 };
        static List<string> produtosVendidos = new List<string>();

        static Dictionary<string, Dictionary<string, object>> informacoesProdutos = new Dictionary<string, Dictionary<string, object>>
        {
            { produto1, new Dictionary<string, object> { { "preco", 2500.00 }, { "marca", "Dell" }, { "garantia", 12 } } },
            { produto2, new Dictionary<string, object> { { "preco", 1200.00 }, { "marca", "Samsung" }, { "garantia", 24 } } },
            { produto3, new Dictionary<string, object> { { "preco", 800.00 }, { "marca", "Apple" }, { "garantia", 12 } } }
        };

        static void MostrarProdutosEstoque()
        {
            Console.WriteLine("📦 Produtos em estoque:");
            foreach (var produto in produtosEstoque)
            {
                Console.WriteLine($"- {produto}");
            }
        }

        static bool VenderProduto(string nomeProduto)
        {
            if (produtosEstoque.Contains(nomeProduto))
            {
                produtosEstoque.Remove(nomeProduto);
                produtosVendidos.Add(nomeProduto);
                Console.WriteLine($"✅ '{nomeProduto}' foi vendido com sucesso!");
                return true;
            }
            else
            {
                Console.WriteLine($"❌ '{nomeProduto}' não está disponível em estoque");
                return false;
            }
        }

        static string InformacoesCompletas(string produto)
        {
            if (informacoesProdutos.ContainsKey(produto))
            {
                var info = informacoesProdutos[produto];
                return $"Preço: R${info["preco"]}, Marca: {info["marca"]}, Garantia: {info["garantia"]} meses";
            }
            else
            {
                return "Produto não encontrado no sistema";
            }
        }

        static void AdicionarProduto(string nome, double preco, string marca = "Genérica", int garantia = 6)
        {
            produtosEstoque.Add(nome);
            informacoesProdutos[nome] = new Dictionary<string, object> 
            { 
                { "preco", preco }, 
                { "marca", marca }, 
                { "garantia", garantia } 
            };
            Console.WriteLine($"📦 '{nome}' foi adicionado ao sistema!");
        }

        static void AdicionarProduto(string nome, double preco)
        {
            AdicionarProduto(nome, preco, "Genérica", 6);
        }

        static void Main(string[] args)
        {
            Console.WriteLine("=== SISTEMA DE GERENCIAMENTO DE PRODUTOS ===");
            MostrarProdutosEstoque();
            Console.WriteLine();
            VenderProduto("Smartphone");
            Console.WriteLine();
            MostrarProdutosEstoque();
            Console.WriteLine($"Produtos vendidos: {string.Join(", ", produtosVendidos)}");
            Console.WriteLine();
            string info = InformacoesCompletas("Tablet");
            Console.WriteLine($"Informações sobre 'Tablet': {info}");
            Console.WriteLine();
            AdicionarProduto("Mouse Gamer", 150.00, "Logitech", 12);
            Console.WriteLine();
            MostrarProdutosEstoque();
            TestarFuncoes();
        }

        static void DevolverProduto(string nomeProduto)
        {
            if (produtosVendidos.Contains(nomeProduto))
            {
                produtosVendidos.Remove(nomeProduto);
                produtosEstoque.Add(nomeProduto);
                Console.WriteLine($"🔄 '{nomeProduto}' foi devolvido e está novamente em estoque!");
            }
            else
            {
                Console.WriteLine($"❌ '{nomeProduto}' não foi encontrado na lista de produtos vendidos");
            }
        }

        static int ContarProdutos()
        {
            return produtosEstoque.Count + produtosVendidos.Count;
        }

        static List<string> BuscarProdutosPorMarca(string marca)
        {
            List<string> produtosDaMarca = new List<string>();
            foreach (var produto in informacoesProdutos)
            {
                if (produto.Value["marca"].ToString().Equals(marca, StringComparison.OrdinalIgnoreCase))
                {
                    produtosDaMarca.Add(produto.Key);
                }
            }
            return produtosDaMarca;
        }

        static void TestarFuncoes()
        {
            Console.WriteLine("\n=== TESTANDO SUAS FUNÇÕES ===");
            Console.WriteLine("\nTestando DevolverProduto:");
            DevolverProduto("Smartphone");
            Console.WriteLine($"\nTotal de produtos no sistema: {ContarProdutos()}");
            Console.WriteLine("\nProdutos da marca Apple:");
            List<string> produtosApple = BuscarProdutosPorMarca("Apple");
            foreach (var produto in produtosApple)
            {
                Console.WriteLine($"- {produto}");
            }
            Console.WriteLine("\n=== SITUAÇÃO FINAL ===");
            MostrarProdutosEstoque();
            Console.WriteLine($"Produtos vendidos: {string.Join(", ", produtosVendidos)}");
        }
    }
}
