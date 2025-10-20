library(shiny)

# Define UI for application that draws a histogram
ui <- fluidPage(
  titlePanel("Hi Babe!"),
  tags$head(
    tags$style(HTML("
      body {
        font-family: 'Times New Roman', sans-serif;
        background: linear-gradient(to bottom, #ffecd2, #fcb69f);
        color: #333;
        text-align: center;
        padding: 50px;
        margin: 0;
      }
      h1 {
        font-size: 3em;
        color: #ff6b6b;
      }
      p {
        font-size: 1.5em;
        margin: 20px 0;
      }
      .message {
        background: rgba(255, 255, 255, 0.8);
        padding: 20px;
        border-radius: 10px;
        box-shadow: 0 0 10px rgba(0,0,0,0.1);
        max-width: 600px;
        margin: 0 auto;
      }
      input {
        padding: 10px;
        font-size: 1em;
        margin: 10px;
        border: 1px solid #ccc;
        border-radius: 5px;
      }
      button {
        padding: 10px 20px;
        font-size: 1em;
        background: #ff6b6b;
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
      }
      button:hover {
        background: #ff5252;
      }
    "))
  ),
  div(class = "message",
      h1("Happy birthday <3"),
      p("Enter our special name:"),
      textInput("name", label = NULL, placeholder = "Enter name"),
      actionButton("generate", "Enter"),
      textOutput("birthdayMessage")
  )
)

# Server (Logika Aplikasi)
server <- function(input, output) {
  output$birthdayMessage <- renderText({
    req(input$generate)  # Tunggu tombol diklik
    name <- input$name
    if (name != "") {
      paste("Happy birthday yang ke 20 dan selamat anniv yg ke 4,", name, "! Maaf ya ucapannya telat dan ga sesuai omongan aku kemarin yang harusnya pagi/siang malah aku kasih besoknya hehe, tapi I just wanna let you know that I love you that much and aku berharap di umur kamu yg ke 20 ini km jadi pribadi yg jauh lebih baik dari sebelumnya, makin bertanggung jawab, dan makin membuat kedua ortu kamu bangga. I'm so happy that we're still together untill now after all that we've been through, and I'm so happy that I'm yours. Semoga di 20 tahun ini kamu jadi lebih bahagia, sehat sehat terus, dan makin bucin ama aku hehe. Gausah panjang panjang ya nanti aku ucapin lagi dan maaf ya ini aku tau masih banyak minus nya WKWKWK tp i try the best for making this web hehe. I love you infinity!❤️")
    } else {
      "Enter your name!"
    }
  })
}


# Run the application 
shinyApp(ui = ui, server = server)
