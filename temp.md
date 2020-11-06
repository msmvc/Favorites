https://blog.csdn.net/beautifull001/article/details/79066411/
https://www.cnblogs.com/wuhuacong/p/5505361.html
https://www.cnblogs.com/mq0036/p/10437993.html


 private void button1_Click(object sender, EventArgs e)
        {
            var client = new RestClient("https://api.apiopen.top/getAllUrl");
           // client.Authenticator = new HttpBasicAuthenticator("username", "password");

            var request = new RestRequest("statuses/home_timeline.json", DataFormat.Json);
            request = new RestRequest();
            var response = client.Get(request);
        }

        private void button2_Click(object sender, EventArgs e)
        {
            var url = "https://api.apiopen.top/getWangYiNews";
            var client = new RestClient(url);
           

           // client.Authenticator = new HttpBasicAuthenticator("username", "password");

           var request = new RestRequest("", Method.POST);
           
            request.AddParameter("page", "1");
            request.AddParameter("count", 5);

            //var param = new { page = "1", count = 5 };
            //request.AddJsonBody(param);


            //var response = client.Execute<Resp>(request);
            //JsonDeserializer js = new JsonDeserializer();
            //var r = js.Deserialize<Resp>(response);

            IRestResponse<Resp> response = client.Execute<Resp>(request);

            var r = response.Data;


        }


        public class Resp
        {
            public int code { get; set; }
            public string message { get; set; }
            public List<Info> result { get; set; }
        }


        public class Info
        {
            public string path { get; set; }
            public string image { get; set; }
            public string title { get; set; }
        }
