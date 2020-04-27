# Projeto.API
System;
using System.Net.Http;
using System.Net;
using System.Threading.Tasks;
using Newtonsoft.Json;

public class Program
{
	public staticvoid Main()
{
		
		var client = new HttpClient();				
		client.BaseAddress = new Uri("http://demo0798384.mockable.io/"); 
		var httpResponse = client.GetAsync("faisp").GetAwaiter().GetResult(); 
		
		Console.WriteLine("Status da consulta na API: {0}\n", httpResponse.StatusCode); 
		
		if(httpResponse.StatusCode !=  HttpStatusCode.OK)
		{
			Console.WriteLine("API indisponível. Tente novamente mais tarde");
			return;		
		}
		
		Console.WriteLine("Resultado da consulta na API\n"); 
		Aluno[] resultado = LerRetorno(httpResponse.Content); 
			Console.WriteLine(resultado);	
		
		
		for(int i = 0;i < resultado.Length; i++)
		{
			Console.Write(resultado[i].nome);
			Console.Write(resultado[i].sobrenome);
			Console.Write(resultado[i].Sala);		
		}	
		
		//Nome          | Sobrenome          | Sala
		
	}
	
	public static Aluno[] LerRetorno(HttpContent content)
	{
		var minhaString = content.ReadAsStringAsync().GetAwaiter().GetResult(); //lemos o response da interação da API e extraímos o retorno na forma de string (texto)
		
		var arrayAlunos = JsonConvert.DeserializeObject<Aluno[]>(minhaString);
		return arrayAlunos;
	
	}
}

public class Aluno
{
   public string nome{get;set;}
   public string sobrenome {get;set;}
   public int Sala {get;set;}	
}  

{ 
Tbl = new DataTable(Aluno);

Tbl.Columns.Add("Nome", typeof(string));

Tbl.Columns.Add("Sobrenome", typeof(string));

Tbl.Columns.Add("Sala", typeof(numeric));

DataRow Linha;

Linha = Tbl.NewRow(1);

Linha[0] = "José";

Linha[1] = "Silva";

Linha[2] = 112;

Linha = Tbl.NewRow(2);

Linha[0] = "Ricardo";

Linha[1] = "Alcatrão";

Linha[2] = 107;

Linha = Tbl.NewRow(3);

Linha[0] = "Carlos";

Linha[1] = "Maranhão";

Linha[2] = 107;

Linha = Tbl.NewRow(4);

Linha[0] = "Paulo";

Linha[1] = "Costa";

Linha[2] = 112;

Linha = Tbl.NewRow(5);

Linha[0] = "Mariaia";

Linha[1] = "Eduarda";

Linha[2] = 105;

Linha = Tbl.NewRow(6);

Linha[0] = "Sabrina";

Linha[1] = "Coelho";

Linha[2] = 118;

Tbl.Rows.Add(Linha);


dataGrid1.GridColumns[6].Alignment = HorizontalAlignment.Right;

}
