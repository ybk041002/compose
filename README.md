import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.Image
import androidx.compose.foundation.layout.*
import androidx.compose.material3.*
import androidx.compose.runtime.Composable
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp

// 만약 ui.theme.Theme.kt 파일에 커스텀 테마를 만들었다면 아래 주석을 해제하세요.
// import com.example.myapplication.ui.theme.ComposeLabTheme
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            // 프로젝트에 ComposeLabTheme가 있다면 아래 코드를 사용하세요.
            // ComposeLabTheme {
            //     MainScreen()
            // }

            // 현재는 기본 MaterialTheme을 사용합니다.
            MaterialTheme {
                MainScreen()
            }
        }
    }
}

@Composable
fun MainScreen() {
    Scaffold(
        topBar = {
            TopAppBar(
                title = { Text("ComposeLab") }
            )
        },
        bottomBar = {
            BottomAppBar {
                Text(
                    text = "우송대",
                    modifier = Modifier.padding(16.dp),
                    fontSize = 16.sp
                )
            }
        }
    ) { innerPadding ->
        Column(
            modifier = Modifier
                .fillMaxSize()
                .padding(innerPadding),
            horizontalAlignment = Alignment.CenterHorizontally,
            verticalArrangement = Arrangement.Center
        ) {
            // 제목
            Text(
                text = "Compose Coffee",
                style = MaterialTheme.typography.headlineMedium,
                modifier = Modifier.padding(bottom = 16.dp)
            )

            // 가게 사진
            // 중요: res/drawable 폴더에 'compose.png' 또는 'compose.jpg' 같은
            // 이미지 파일이 실제로 있는지 확인해야 합니다.
            Image(
                painter = painterResource(id = R.drawable.compose),
                contentDescription = "Compose Coffee 매장",
                modifier = Modifier
                    .size(250.dp)
                    .padding(16.dp)
            )

            // 버튼 두 개 (Row 배치)
            Row(
                modifier = Modifier.padding(8.dp),
                horizontalArrangement = Arrangement.spacedBy(16.dp)
            ) {
                Button(onClick = { /* 커피 주문 로직 구현 */ }) {
                    Text("커피 주문")
                }
                Button(onClick = { /* 쥬스 주문 로직 구현 */ }) {
                    Text("쥬스 주문")
                }
            }

            // 위치 안내 텍스트
            Text(
                text = "위치: 우송대 정문 앞",
                style = MaterialTheme.typography.bodyLarge,
                modifier = Modifier.padding(top = 16.dp)
            )
        }
    }
}

@Preview(showBackground = true)
@Composable
fun PreviewMainScreen() {
    MaterialTheme {
        MainScreen()
    }
}
